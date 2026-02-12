---
uid: Connector_help_SES_Service_Problem_Management_Technical
---

# SES Service Problem Management

## About

The SES Service Problem Management connector implements bidirectional integration with SNOW systems using the TMF656 Service Problem Management API and TMF642 Alarm Management API standards. The connector synchronizes DataMiner tickets with external service problems, automating ticket lifecycle management through RESTful API communications over HTTPS.

### Version Info

| Range              | Key Features                                                                                                                                                                             | Based on | System Impact                                       |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | --------------------------------------------------- |
| 1.0.0.x            | Initial version. Protocol uses Unicode. Multi-threaded ticket creation with 5 concurrent processing threads. TMF656/TMF642 API integration.<br>**Requires DataMiner Ticketing license**. | -        | -                                                   |
| 2.0.0.x [SLC Main] | Migration to SDM Ticketing (`TicketingApiHelper`). Uses `TicketType` with `FieldDefinition` for schema definition and `TicketField` for custom field management.                         | 1.0.0.x  | Requires `DataMiner SDM Ticketing Module` solution. |

### Product Info

| Range   | Supported Firmware       |
| ------- | ------------------------ |
| 1.0.0.x | TMF656 v1.0, TMF642 v1.0 |
| 2.0.0.x | TMF656 v1.0, TMF642 v1.0 |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components              | Exported Components |
| ------- | --------------- | ------------------- | ------------------------------ | ------------------- |
| 1.0.0.x | No              | Yes                 | DataMiner Ticketing module     | -                   |
| 2.0.0.x | No              | Yes                 | DataMiner SDM Ticketing module | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the SES Service Problem Management API destination.
- **IP port**: The IP port of the destination (default: _443_).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify _BypassProxy_.

### Initialization

To initialize the connector, navigate to the **Configuration** page of the element and configure the following mandatory parameters:

- **API Base Path**: The base REST API endpoint path (default: `gstm/dataminer/tmf/api/v1/tmf656/`).
- **Username**: The authentication username for API access.
- **Password**: The authentication password (masked field).
- **Ticket Synchronization State**: Enable or disable ticket synchronization (default: _Enabled_).
- **Tickets Synchronization Frequency**: Set the interval between synchronization cycles (range: 10-86400 seconds, default: 60 seconds).

On first startup, the connector automatically initializes:

- A **TicketType** named "SES" with all required `FieldDefinition` objects for ticket schema definition.
- An **ExternalOwner** named "ServiceNow" with the appropriate `VisualizationEndpoint` and `ApiEndpoint`.

All tickets managed by this connector use the single "SES" TicketType.

## How to use

### General Page

The **General** page provides operational visibility on ticket management:

- **Managed Tickets Number**: Displays the total count of currently managed tickets in the system.
- **Tickets Table**: Comprehensive table listing all synchronized tickets, with the following columns:
  - **DataMiner Ticket ID**: Unique identifier from the DataMiner SDM Ticketing system.
  - **DataMiner Ticket Info**: Serialized JSON representation of the complete ticket object.
  - **Service Problem ID**: Corresponding service problem ID in the SNOW system.
  - **Service Problem Incident Number**: Human-readable incident number for reference.
  - **Service Problem Incident Link**: Direct URL link to the service problem in the SNOW interface.

The table supports filtering, sorting, and pagination (25 rows per page), with partial loading for performance optimization.

### Configuration Page

The **Configuration** page contains all configurable parameters for connector operation:

- **Ticket Synchronization State**: Toggle button to enable/disable the ticket synchronization engine.
- **Tickets Synchronization Frequency**: Slider control to adjust synchronization interval (10 seconds to 24 hours).
- **API Base Path**: Text field for configuring the base API endpoint URL.
- **Username**: Text field for API authentication username.
- **Password**: Masked password field for API authentication.

### Synchronization Workflow

The connector executes a comprehensive synchronization workflow at each interval:

1. **Update table entries**: Retrieves active DataMiner tickets using the `TicketingApiHelper` (filtering by status: _New_, _Assigned_, _In Progress_, _On Hold_) and updates the local table with current ticket information.

1. **Create new service problems**: Identifies tickets without an associated Service Problem ID and creates new service problems via POST requests to the `serviceProblem` endpoint using multithreaded processing (5 concurrent threads).

1. **Create new event problems**: Detects tickets with cleared Device IP Address fields and creates corresponding event problems via POST requests to the TMF642 alarm endpoint for device-level correlation.

1. **Close service problems**: Monitors tickets for closure triggers (RestoredBy field set to "ses_group") and sends PATCH requests to update service problems to resolved status.

1. **Update old service problems**: Compares stored ticket JSON with current ticket state to detect changes, then sends PATCH requests for tickets with state, priority, or field modifications.

### API Integration Details

#### Authentication

The connector uses HTTP Basic Authentication for all API requests. Credentials are configured on the Configuration page and applied to all HTTP sessions.

#### HTTP Sessions

The connector implements 8 distinct HTTP sessions:

- **Session 101 (GET)**: Retrieves service problems updated since the last synchronization.
  - Endpoint: `serviceProblem?sysparm_query=u_source=dataminer^sys_updated_on>=<timestamp>`
  - Purpose: Poll for external changes to service problems.

- **Sessions 102-106 (POST)**: Creates service problems with parallel processing.
  - Endpoint: `serviceProblem`
  - Connections: 5 concurrent threads (default connection + 1001-1004)
  - Headers: `Content-Type: application/json`, `Accept: application/json`

- **Session 107 (PATCH)**: Updates existing service problems.
  - Endpoint: `serviceProblem/{id}`
  - Purpose: Synchronize ticket state changes.

- **Session 108 (POST)**: Creates event problems for device-level alarms.
  - Endpoint: `gstm/dataminer/tmf/api/v1/tmf642/alarm`
  - Purpose: Establish alarm-to-service correlation.

#### Response Processing

All HTTP responses are validated for successful status codes (2xx range). The connector:

- Parses JSON response bodies to extract service problem IDs and incident numbers.
- Updates DataMiner ticket fields with service problem information using `SetTicketFieldValue` on the `TicketField` model.
- Sets alarm properties (SNOW Ticket UID, SNOW Incident Number, SNOW Incident Link) via SLNet messaging.
- Updates the Tickets Table with synchronized data.

### Multithreading Architecture

The connector employs a sophisticated multithreading strategy for optimal performance:

- **Thread dispatcher**: Manages 5 concurrent processing slots for service problem creation.
- **Request buffering**: Queues ticket creation requests when all threads are occupied.
- **Connection pooling**: Utilizes 5 HTTP connections (default + 1001-1004) for parallel POST operations.
- **Thread safety**: Implements proper locking and synchronization mechanisms to prevent race conditions.

## Notes

### SDM Ticketing Dependency

This connector requires the **DataMiner SDM Ticketing** solution to function. The connector uses the `TicketingApiHelper` class to retrieve, create, and update tickets through the SDM Ticketing API.

### Ticket Schema

The connector defines an "SES" `TicketType` on startup with all required `FieldDefinition` objects. Custom ticket fields are managed through `TicketField` instances rather than the legacy `CustomTicketFields` dictionary. Fields are accessed and updated using the `SetTicketFieldValue` helper pattern.

### Performance Considerations

- **Synchronization frequency**: Setting very low synchronization intervals (below 30 seconds) in high-volume environments may impact system performance. Monitor CPU and network utilization when adjusting this parameter.

- **Concurrent threads**: The connector is configured with 5 concurrent processing threads. This limit balances performance with API rate limiting constraints. Do not modify connection counts without consulting API rate limit documentation.

### Integration Standards

The connector adheres to:

- **TMF656**: Service Problem Management API v1.0.
- **TMF642**: Alarm Management API v1.0.
- **ISO 8601**: Date/time formatting standard.
- **RESTful Principles**: HTTP methods (GET, POST, PATCH) for resource manipulation.

### Alarm Property Updates

The connector sets alarm properties on the originating alarms to establish bidirectional links:

- **SNOW Ticket UID**: Links alarm to DataMiner ticket.
- **SNOW Incident Number**: Provides human-readable incident reference.
- **SNOW Incident Link**: Offers direct navigation to service problem.

### Minimum DataMiner Version

This connector requires **DataMiner 10.5.0** or higher because of dependencies on:

- SDM Ticketing APIs (`TicketingApiHelper`).
- The **DataMiner SDM Ticketing** solution must be available on the DataMiner system.
