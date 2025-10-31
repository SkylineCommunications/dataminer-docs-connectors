---
uid: Connector_help_SES_Inventory_Management_Technical
---

# SES Inventory Management

## About

The SES Inventory Management connector is a DataMiner HTTP-based protocol that integrates with SNOW system and interfaces with TMF 638 (Service Inventory Management) and TMF 639 (Resource Inventory Management) APIs. It retrieves and monitors customer-facing services, carrier elements, and network resources, maintaining a synchronized cache of inventory data through periodic polling.

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

- **TMF 638 Username/Password**: Credentials for basic authentication to TMF 638 API (Services and Carriers).
- **TMF 639 Endpoint**: The full endpoint URL for TMF 639 API (default: `https://mintapi.dbb-oa-dev.az.ses/gstm/dataminer/tmf/api/v1/tmf639`).
- **TMF 639 Username/Password**: Credentials for basic authentication to TMF 639 API (Resources).
- **Cache Update Frequency**: Polling interval in seconds (default: 3600 seconds, range: 3600-432000 seconds).

### Redundancy

Redundancy is not defined in this connector.

## How to use

The connector operates in two modes:

**Initial Cache Buildup**: On element startup, the connector performs paginated retrieval of all inventory items (40 records per page) for Services, Carriers, and Resources. This process continues until all pages are retrieved.

**Periodic Cache Updates**: After initial buildup, the connector periodically polls for items updated in the last 24 hours (`updatedDaysAgo=0`) based on the configured Cache Update Frequency.

### Services Page

Displays customer-facing services (CFS) retrieved from TMF 638 API with the following columns:

- External ID, Name, Description
- Status, Type
- Start Date, End Date, Last Update
- Related Party, Location
- Service Specification, Supporting Resources

### Carriers Page

Shows carrier elements retrieved from TMF 638 API filtered by `@type=element`, presenting:

- External ID, Name, Description
- Status, Type
- Creation Date, Last Update
- Service Characteristics
- Supporting Services

### Resources Page

Lists network resources from TMF 639 API including:

- External ID, Name, Description
- Status, Type
- Resource Specification
- Resource Characteristics
- Related Parties, Locations
- Resource Relationships

### Configuration Page

Provides parameters for API endpoint configuration, authentication credentials, and cache update frequency settings.

## Notes

- The connector requires minimum DataMiner version 10.3.0.0 (build 12752).
- All API requests use basic authentication with separately configurable credentials for TMF 638 and TMF 639 endpoints.
- The connector filters services and resources by `status=1` to retrieve only active items.
- Pagination uses `recordsPerPage=40` for optimal performance during cache buildup.
