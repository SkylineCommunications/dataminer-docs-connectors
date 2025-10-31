---
uid: Connector_help_SES_Inventory_Management
---

# SES Inventory Management

## About

The SES Inventory Management connector integrates with SNOW system to retrieve and monitor satellite communication services, carriers, and network resources. It interfaces with TMF 638 (Service Inventory Management) and TMF 639 (Resource Inventory Management) APIs to provide visibility into the operational status and configuration of communication elements.

## Key Features

- **Service Inventory Retrieval**: Retrieves and displays customer-facing services (CFS) with detailed characteristics, supporting resources, and related parties.

- **Carrier Management**: Monitors carrier elements including status, location, service specifications, and hierarchical relationships.

- **Resource Tracking**: Accesses network resources with characteristics, specifications, and relationships through TMF 639 API integration.

- **Automated Cache Management**: Periodic cache updates with configurable frequency to maintain synchronized inventory data.

- **Paginated Data Retrieval**: Efficiently handles large datasets using pagination with 40 records per page for optimal performance.

## Use Cases

### Use Case 1

**Challenge**: Operations teams need centralized visibility into all active customer-facing services across the satellite network infrastructure.

**Solution**: The connector retrieves service inventory data from TMF 638 API, displaying services with their status, locations, related parties, and supporting resources in an organized table format.

**Benefit**: Enables quick identification of service configurations and dependencies, reducing troubleshooting time and improving operational awareness.

### Use Case 2

**Challenge**: Network operators require real-time monitoring of carrier elements and their operational status to maintain service quality.

**Solution**: The connector polls carrier information including status, service characteristics, and relationships, presenting a comprehensive view of all carrier elements.

**Benefit**: Facilitates proactive monitoring and rapid response to carrier issues, minimizing service disruptions.

## Technical Reference

### Prerequisites

- **TMF 638 API Access** is needed for retrieving services and carriers with valid authentication credentials.

- **TMF 639 API Endpoint** is required for accessing resource inventory data.

- **Network Connectivity** to SES inventory management APIs over HTTPS (port 443).

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_SES_Inventory_Management_Technical).
