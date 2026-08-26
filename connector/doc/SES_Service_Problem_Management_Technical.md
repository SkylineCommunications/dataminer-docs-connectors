---
uid: Connector_help_SES_Service_Problem_Management_Technical
---

# SES Service Problem Management

## About

The SES Service Problem Management connector implements bidirectional integration with SNOW systems using the TMF656 Service Problem Management API and TMF642 Alarm Management API standards. The connector synchronizes DataMiner tickets with external service problems, automating ticket lifecycle management through RESTful API communications over HTTPS.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the SES Service Problem Management API destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

To initialize the connector, navigate to the **Configuration** page of the element and configure the following mandatory parameters:

- **API Base Path**: The base REST API endpoint path (default: `gstm/dataminer/tmf/api/v1/tmf656/`).
- **Username**: The authentication username for API access.
- **Password**: The authentication password (masked field).
- **Ticket Synchronization State**: Enable or disable ticket synchronization (default: *Enabled*).
- **Tickets Synchronization Frequency**: Set the interval between synchronization cycles (range: 10-86400 seconds, default: 60 seconds).

On first startup, the connector will automatically initialize the following:

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
  - **Creation Status**: Tracks the ticket's SNOW creation lifecycle (`None`, `Buffered`, `Created`). Set to *Buffered* when the ticket is received and awaiting SNOW creation, set to *Created* when confirmed by SNOW, and reset to *None* on failure for retry.

The table supports filtering, sorting, and pagination (25 rows per page), with partial loading for performance optimization.

### Configuration Page

The **Configuration** page contains all configurable parameters for connector operation:

- **Ticket Synchronization State**: Toggle button to enable/disable the ticket synchronization engine.
- **Tickets Synchronization Frequency**: Slider control to adjust synchronization interval (10 seconds to 24 hours).
- **API Base Path**: Text field for configuring the base API endpoint URL.
- **Username**: Text field for API authentication username.
- **Password**: Masked password field for API authentication.

### Ticket Creation Subscription

The connector subscribes to the DataMiner SDM Ticketing module's `OnCreated` event at startup (when synchronization is enabled). When a new SES ticket is created anywhere in the DMS:

1. The subscription callback fires in real time.
1. The ticket is validated against the "SES" `TicketType`. Non-SES tickets are ignored.
1. The ticket is added to the Tickets Table with a **Buffered** creation status.
1. The ticket ID is appended to the creation buffer, and SNOW service problem creation is triggered immediately.

The subscription is automatically enabled or disabled based on the **Ticket Synchronization State** toggle button. A periodic refresh (every hour, with a 10-minute minimum interval) ensures the internal `SLProtocol` reference and `TicketingApiHelper` connection remain valid. All table access during subscription callbacks is synchronized via a shared lock to prevent race conditions with the polling-based synchronization path.

### Synchronization Workflow

The connector executes a comprehensive synchronization workflow at each interval:

1. **Update table entries**: Retrieves active DataMiner tickets using the `TicketingApiHelper` (filtering by status: *New*, *Assigned*, *In Progress*, *On Hold*) and updates the local table with current ticket information.

1. **Create new service problems**: Identifies tickets in the creation buffer without an associated Service Problem ID and creates new service problems via POST requests to the `serviceProblem` endpoint using multithreaded processing (5 concurrent threads). Buffer access is synchronized with the ticket creation subscription using a shared lock to prevent race conditions. Each thread tracks its assigned ticket ID, and on failure the ticket's Creation Status is reset to *None* for retry.

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
- **Thread tracking**: Each processing slot tracks the ticket ID it is handling via a `ConcurrentDictionary`. On failure, the tracked ticket ID is used to reset the Creation Status, ensuring the ticket is retried. The tracking entry is cleaned up in the `finally` block after thread release.

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

### Event-Based Ticket Ingestion

The 1.1.0.x range introduces an event-based ticket ingestion path alongside the existing polling mechanism. Key implementation details:

- **Subscription lifecycle**: Managed via dedicated dummy parameters (PIDs 6, 7, 8) for refresh, enable, and disable operations. The subscription is enabled at startup when synchronization is active and disabled when synchronization is turned off.
- **Thread safety**: A `TableSynchronizationLock` ensures that the subscription callback and the polling-based synchronization do not concurrently modify the Tickets Table or creation buffer. Buffer reads and writes inside `BuildCreateServiceProblem` now operate under the same lock.
- **Creation Status tracking**: A new column (PID 1006) tracks each ticket's state through the creation pipeline: `None` (0) → `Buffered` (1) → `Created` (2). On SNOW creation failure, the status is reset to `None` so the ticket is retried on the next synchronization cycle.
- **Batched alarm property updates**: The `SetAlarmProperties` method replaces individual `SetAlarmProperty` calls, batching all property updates for a ticket (SNOW Ticket UID, Incident Number, Incident Link) into a single `SendMessages` SLNet call for improved performance.

### Minimum DataMiner Version

This connector requires **DataMiner 10.5.0** or higher because of dependencies on:

- SDM Ticketing APIs (`TicketingApiHelper`).
- The **DataMiner SDM Ticketing** solution, which must be available on the DataMiner System.
