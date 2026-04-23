---
uid: Connector_help_EVS_IPD-VIA_Technical
---

# EVS IPD-VIA

## About

The EVS IPD-VIA connector integrates DataMiner with the EVS IPD-VIA platform via the OpenGate v2 REST API and RabbitMQ message queues. It retrieves recorders, targets, profiles, and recording sessions from the API, and subscribes to the RabbitMQ recording session queue to receive live updates without polling. Recording sessions can also be created, updated, and deleted externally via the DataMiner InterApp framework.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the EVS IPD-VIA platform.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

After the element has been created, configure the following on the **Configuration** page before the connector will start retrieving data.

**API credentials:**

- **Username**: The username used to authenticate against the OpenGate API.
- **Password**: The password used to authenticate against the OpenGate API.

Once valid credentials are provided, the **API Connection** status will update to confirm a successful login.

**RabbitMQ connection:**

- **RabbitMQ Host**: The hostname or IP address of the RabbitMQ server.
- **RabbitMQ Port**: The port used to connect to RabbitMQ (default: *5671*).
- **RabbitMQ Username**: The username for RabbitMQ authentication.
- **RabbitMQ Password**: The password for RabbitMQ authentication.
- **RabbitMQ Virtual Host**: The RabbitMQ virtual host to connect to.

Once the RabbitMQ connection parameters are configured, the **RabbitMQ Connection** status will reflect the connection state.

## How to Use

### General Page

The **Recording Sessions** table provides an overview of all ongoing and scheduled recording sessions retrieved from EVS IPD-VIA. Each row shows the session name, status, start and end times, and the associated recorder. Sessions are updated in real time via RabbitMQ and also refreshed periodically through the API.

The **Recording Session Removal Delay** parameter controls how long a completed session remains visible in the table before it is automatically removed.

### Recorders Page

The **Recorders** table lists all recorders available in the EVS system, including their name, status, and server. Use the **Refresh Recorders** button to manually trigger a refresh from the API.

### Targets Page

The **Targets** table lists all available ingest targets and their workflow definition names. The **Targets Configuration** subtable allows parameters to be associated with specific targets for use when building recording session requests.

Use the **Refresh Targets** button to manually trigger a refresh from the API.

### Metadata Page

This page contains four tables that expose the metadata model used by EVS IPD-VIA:

- **Profiles**: All metadata profiles available in the system, including type, status, and fully qualified name (FQN).
- **Profile Fields**: The individual fields belonging to each profile, including key, label, type, and any value constraints.
- **Recording Sessions Profiles**: The profiles associated with each recording session.
- **Recording Sessions Metadata Values**: The individual metadata key-value pairs attached to each recording session.

### Configuration Page

This page contains all connection and authentication settings for both the API and RabbitMQ, as described in the [Initialization](#initialization) section. It also provides:

- **Debug Logging**: When enabled, additional diagnostic information about InterApp and RabbitMQ communication is written to an external log file at `C:\Skyline_Data\EVS_IPD_VIA_Logging\`.

### InterApp

Recording sessions can be created, updated, and deleted by external DataMiner Automation scripts using the InterApp framework. The required message types are provided by the `Skyline.DataMiner.ConnectorAPI.EVS.IPD-VIA` NuGet package, which must be referenced by any script that sends messages to this connector.

Two message types are supported:

- **AddOrUpdateRecordingSession**: Creates a new scheduled recording session or updates an existing one. The connector routes the request to the correct OpenGate v2 endpoint based on the current session status — scheduled sessions are managed via `/schedules`, while ongoing sessions are managed via `/recording-sessions`.
- **DeleteRecordingSession**: Deletes an existing recording session. As with updates, the correct endpoint is selected automatically based on the session's current status.

When the API responds, the connector sends the result back to the originating source of the InterApp message, including a success flag and, in case of failure, an error message.

## Notes

### Version Info

| Range | Key Features | Based on | System Impact |
|---|---|---|---|
| 1.0.0.x | Initial version. OpenGate v1 API. | - | - |
| 2.2.0.x [SLC Main] | Migrated to OpenGate v2 API. Scheduled and ongoing sessions are routed to separate endpoints based on session status. | 1.0.0.x | Requires EVS VIA MAP 1.1 or higher. |

### Product Info

| Range | Supported Firmware |
|---|---|
| 1.0.0.x | RabbitMQ 3.8.5 |
| 2.2.0.x | OpenGate API v2 (EVS VIA MAP 1.1+), RabbitMQ 3.8.5 |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---|---|---|---|---|
| 1.0.0.x | No | Yes | - | - |
| 2.2.0.x | No | Yes | - | - |
