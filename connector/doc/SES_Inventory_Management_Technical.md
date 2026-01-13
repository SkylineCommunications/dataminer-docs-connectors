---
uid: Connector_help_SES_Inventory_Management_Technical
---

# SES Inventory Management

## About

The SES Inventory Management connector is an HTTP-based DataMiner connector that integrates with the SNOW system and interfaces with the TMF 638 (Service Inventory Management) and TMF 639 (Resource Inventory Management) APIs. It retrieves and monitors customer-facing services, carrier elements, and network resources, storing all data in [DataMiner Object Models (DOM)](https://aka.dataminer.services/DOM) instances for structured data management.

The connector maintains a synchronized cache of inventory data through periodic polling and implements intelligent update logic with duplicate handling and status preservation.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the SES inventory management API endpoint.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

After creating the element, configure the following parameters on the **Configuration** page:

- **TMF 638 Username/Password**: Credentials for basic authentication to TMF 638 API (services and carriers).
- **TMF 639 Endpoint**: The full endpoint URL for TMF 639 API (default: `https://mintapi.dbb-oa-dev.az.ses/gstm/dataminer/tmf/api/v1/tmf639`).
- **TMF 639 Username/Password**: Credentials for basic authentication to TMF 639 API (resources).
- **Cache Update Frequency**: The polling interval in seconds (default: 3600 seconds, range: 3600-432000 seconds).

### DOM Definitions

The connector automatically creates the following DOM definitions on first run:

- **Services**: Stores customer-facing services with characteristics, locations, and relationships.
- **Carriers**: Stores carrier elements with operational status, service characteristics, and supporting resources.
- **Resources**: Stores network resources with specifications, characteristics, and relationships.

## How to use

The connector operates in two modes:

- **Initial cache buildup**: On element startup, the connector performs paginated retrieval of all inventory items (50 records per page) for services, carriers, and resources. This process continues until all pages have been retrieved. During cache buildup, the connector tracks entity IDs across pages and performs cleanup of deprecated items only on the final page.

- **Periodic cache updates**: After initial buildup, the connector periodically polls for items updated in the last 24 hours (`updatedDaysAgo=0`) based on the configured Cache Update Frequency. For services, cleanup of non-operational services runs every time data are polled after the initial cache buildup is completed.

### DOM Storage Architecture

#### Services Repository

- **Entity ID**: Uses `service.ExternalId` as the unique identifier.
- **Deduplication**: Removes duplicate external IDs from API responses before processing.
- **Status Tracking**: Maps operational status from `service.Status` API field.
- **Cleanup Logic**: Removes services where operational status is not "Operational" every time data are polled after initial cache buildup.
- **Field Mapping**:
  - Basic fields: ID, Name, Description, Status, Type
  - Temporal fields: Start Date, End Date, Last Update
  - Related Party: Extracts customer role from related parties
  - Location: Site information from place fields
  - Service Characteristics: Custom characteristics from API
  - Supporting Resources: Linked resources

#### Carriers Repository

- **Entity ID**: Uses `carrier.ExternalId` as the unique identifier.
- **Deduplication**: Filters out carriers with null/empty external IDs and removes duplicates.
- **Cleanup Logic**: Removes deprecated carriers only during final page of cache buildup.
- **Field Mapping**:
  - Basic fields: ID, Name, Operational Status
  - Location fields: Gateway, Terminal
  - Service Characteristics: ElementType, Type (from "type" characteristic), Uplink/Downlink aliases, RF center frequencies
  - Supporting Resources: Satellite and Transponder information
  - Supporting Services: Bandwidth segments from CFS services with "Operational" status

#### Resources Repository

- **Entity ID**: Uses `resource.Id` as the unique identifier.
- **Type Filtering**: Excludes the following resource types before DOM processing: Card, BandwidthSegment, LogicalPort, Multicast, Slot, Port, Circuit
- **Status Preservation**: For modem resources, preserves existing operational status during updates to maintain continuity.
- **Cleanup Logic**: Removes deprecated resources only during final page of cache buildup.
- **Field Mapping**:
  - Basic fields: ID, Name, Description, Status (preserved for modems)
  - Resource Specification: Type and specification details
  - Resource Characteristics: Custom characteristics from API
  - Related Parties: Associated parties
  - Locations: Physical locations
  - Resource Relationships: Hierarchical relationships

### Cache Buildup Pattern

All three entity types follow this pattern during initial cache buildup:

1. **Page Processing**: API responses are processed page by page (50 records per page).
1. **ID Tracking**: Entity IDs are accumulated across pages in a dedicated parameter:
   - Services: `Parameter.servicesids_4998`
   - Carriers: `Parameter.carriersids_2998`
   - Resources: `Parameter.resourcesids_3998`
1. **Continuation**: If a page is full (`services.Length == Global.RecordsPerPage`), the next page is triggered.
1. **Final Page**: When a partial page is received:
   - Cleanup of deprecated entities is performed (except services).
   - The cache buildup flag is cleared.
   - The ID tracking parameter is cleared.

### Configuration Page

This page contains parameters for the API endpoint configuration, authentication credentials, cache update frequency settings, and DOM instance counts.

## DOM Implementation Details

### Benefits of DOM Storage

- **Structured data**: Field-level validation and type safety through section definitions.
- **Scalability**: Efficient querying and filtering using DOM queries instead of table scans.
- **Data integrity**: Built-in deduplication and validation logic.
- **Flexibility**: Easy to extend with new fields without protocol changes.
- **Relationships**: Native support for entity relationships and references.

### Data Synchronization

The connector implements a two-phase approach:

1. **Create or Update**: Incoming API data is compared against existing DOM instances by external ID:
   - If an instance already exists, all fields are updated via mapper.
   - If the instance is new, a new DOM instance is created with mapped fields.

1. **Cleanup**: Deprecated entities (not in the current API response) are removed:
   - Carriers/Resources: Only during the final cache buildup.
   - Services: Whenever data are polled after cache buildup is completed.

### Error Handling

- **Null/Empty IDs**: Entities with null or empty external IDs are skipped with logging.
- **Duplicate IDs**: The first occurrence is kept; duplicates are logged and skipped.
- **Batch Processing**: DOM operations are batched (100 instances per batch) for optimal performance.
- **Failure Tracking**: Failed operations are logged with success/failure counts.

## Notes

- The connector requires **DataMiner 10.5.0** or higher.
- The **DOM module** must be available and accessible for the connector to create definitions and instances.
- All API requests use basic authentication with separately configurable credentials for TMF 638 and TMF 639 endpoints.
- The connector filters services and resources by `status=1` to retrieve only active items.
- Pagination uses `recordsPerPage=50` for optimal performance during cache buildup.
- Duplicate external IDs are automatically handled. The first occurrence is kept; subsequent duplicates are skipped.
- Modem status is preserved during resource updates to maintain operational continuity.
- Cleanup of services runs every time data are polled after cache buildup, while cleanup of carriers and resources only happens during cache buildup.
