---
uid: Connector_help_SES_Inventory_Management
---

# SES Inventory Management

## About

The SES Inventory Management connector integrates with the SNOW system to retrieve and monitor satellite communication services, carriers, and network resources. It interfaces with the TMF 638 (Service Inventory Management) and TMF 639 (Resource Inventory Management) APIs to provide visibility on the operational status and configuration of communication elements.

Data is stored using DataMiner's **DataMiner Object Model (DOM)** for enhanced scalability, flexibility, and data integrity.

## Key Features

- **Service inventory retrieval**: Retrieves and displays customer-facing services (CFS) with detailed characteristics, supporting resources, and related parties.
- **Carrier management**: Monitors carrier elements including status, location, service specifications, and hierarchical relationships.
- **Resource tracking**: Accesses network resources with characteristics, specifications, and relationships through TMF 639 API integration.
- **DOM-based storage**: Leverages DataMiner Object Model for structured data management with built-in validation.
- **Automated cache management**: Uses periodic cache updates with configurable frequency to maintain synchronized inventory data.
- **Paginated data retrieval**: Efficiently handles large datasets using pagination with 40 records per page for optimal performance.
- **Duplicate handling**: Automatically de-duplicates entities based on ExternalId to ensure data integrity.

## Use Cases

### Instant Insight in Services

**Challenge**: Operations teams need centralized visibility on all active customer-facing services across the satellite network infrastructure.

**Solution**: The connector retrieves service inventory data from TMF 638 API and stores it in DOM instances, providing structured access to services with their status, locations, related parties, and supporting resources.

**Benefit**: Enables quick identification of service configurations and dependencies through DOM queries, reducing troubleshooting time and improving operational awareness.

### Real-Time Carrier Monitoring

**Challenge**: Network operators require real-time monitoring of carrier elements and their operational status to maintain service quality.

**Solution**: The connector polls carrier information including status, service characteristics, and relationships, storing them as structured DOM instances with proper field validation.

**Benefit**: Facilitates proactive monitoring and rapid response to carrier issues through efficient DOM-based queries, minimizing service disruptions.

### Resource Lifecycle Management

**Challenge**: Network teams need to track resource status changes while preserving operational context (e.g., modem status during updates).

**Solution**: The connector implements intelligent update logic that preserves critical operational states (like modem status) during resource updates from the API.

**Benefit**: Maintains operational continuity while keeping resource data synchronized with the inventory system.

## Prerequisites

- This connector requires **DataMiner 10.5.0** or higher.
- **DOM** is required for creating and managing DOM definitions and instances.
- **TMF 638 API Access** is needed for retrieving services and carriers with valid authentication credentials.
- **TMF 639 API Endpoint** is required for accessing resource inventory data.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_SES_Inventory_Management_Technical).