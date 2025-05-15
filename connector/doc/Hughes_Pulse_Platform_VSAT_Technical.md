---
uid: Connector_help_Hughes_Pulse_Platform_VSAT_Technical
---

# Hughes Pulse Platform VSAT

## About

The Hughes Pulse Platform VSAT connector integrates remote terminal data from the Hughes Pulse API into DataMiner. It retrieves device status, performance metrics (ICMP, signal strength, throughput), usage data, and configuration details by polling HTTP endpoints.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: `https://api.hugheson.net`
- **IP port**: `443` (default)

### Initialization

When the element has been created, configure the credentials to connect to the Hughes Pulse API:

1. Set the following parameters on the **Configuration** page:

   - **REST API Username**
   - **REST API Password**
   - **Maximum Login Retries**

1. Use the **Login** button to manually initiate authentication.

When the login is successful, a token will be generated and stored, and the **Token Expiration** parameter will be updated accordingly.

## How to Use

The connector auto-configures itself to poll default endpoints based on the API's capabilities.

### Automatically Added Endpoints

Upon element startup, the connector adds the following to the **REST API Endpoints Configuration** table (shown on a subpage of the **Configuration** page):

| HTTP Verb | Endpoint                                                  | Category | Timer   | Batch Size |
|-----------|-----------------------------------------------------------|----------|---------|------------|
| GET       | `assets/device?san=*`                                     | Remotes  | 30 min  | N/A        |
| GET       | `assets/device?san=*&fields=["name","state"]`             | Remotes  | 5 min   | N/A        |
| POST      | `telemetry/metrics?metric_name=icmp`                      | Metrics  | 5 min   | 100        |
| POST      | `telemetry/metrics?metric_name=signalStrength`            | Metrics  | 5 min   | 100        |
| POST      | `telemetry/metrics?metric_name=throughput`                | Metrics  | 5 min   | 100        |
| POST      | `usagedata`                                               | Usage    | 1 hour  | 5          |

The following configuration options are available for each entry:

- Polling interval
- Enable/disable polling
- Display last API response
- Manual **Poll** button
- HTTP verb (GET or POST)
- Custom POST body content
- Configurable batch size (splits the device list into smaller independent POST requests)

> [!NOTE]
> The **Batch Size** defines how many devices are included in each separate POST request. Batching is used to:
>
> - Prevent timeout or server errors (e.g., 504 or 500) on large payloads  
> - Avoid paginating API responses  
> - Ensure partial failures don’t block polling (failed batches are retried individually)

> [!IMPORTANT]
> You can add additional endpoints for testing, categorized as *N/A*. However, be careful when editing the automatically added endpoints, as they populate the **Remotes**, **Metrics**, and **Usage** tables:
>
> - You can apply filters to the POST body to reduce the number of returned remotes.
> - **Do not change the *Category*** of the default endpoints. Changing it to anything other than *Remotes*, *Metrics*, or *Usage* will keep the corresponding table from being populated. If this does happen, remove the affected row from the table and restart the element. This will recreate the row with the default values.

#### Default POST Body (Metrics & Usage)

Below is the default POST body used for the metric endpoints (`icmp`, `signalStrength`, `throughput`):

```json
{
    "devices": "__REPLACE_DEVICES__",
    "filter": [],
    "time_choice": "1 day",
    "offset": 0,
    "pagesize": "__REPLACE_PAGESIZE__",
    "sort": "",
    "sortOrder": "asc"
}
```

- __REPLACE_DEVICES__ is replaced at runtime with the list of remote device IDs.
- __REPLACE_PAGESIZE__ is replaced by the defined Batch Size.
- time_choice can be customized:
  - For Metrics, it defaults to "1 day"
  - For Usage, it defaults to "30 days" but can be set to "1 day" or "7 days" as needed.

### Pages Overview

Below you can find more information about the other data pages available in the element.

#### General Page

This page displays the total number of remotes discovered.

#### Remotes Page

The table on this page is populated via the `assets/device` endpoints. It includes fields such as Device ID, Access Mode, Location, and Status.

#### Metrics Page

The table on this page is populated via the `telemetry/metrics` POST endpoints.

It contains timestamped values for:

- **ICMP**: Latency, Packet Loss, Jitter, Availability
- **Signal Strength**: RSRP, RSSI, SINR
- **Throughput**: Avg Total Up, Avg Total Down

### Daily Data Usage Page

This page is populated by the `usagedata` POST endpoint and displays daily traffic statistics per device.

Each row represents usage data for a unique combination of:

- **Device ID**
- **Usage Category**
- **Date**

The following metrics are displayed:

- **Inbound**: Amount of data received in MB
- **Outbound**: Amount of data sent in MB
- **Total**: Sum of inbound and outbound in MB
- **Timestamp**: Date of the measurement

Each device can report multiple usage categories (e.g., Web Browsing, Entertainment, Network Infrastructure), which are derived from the Hughes API and may vary.

> [!NOTE]
> The retention period for this data is configured on the **Collector Setup** page, where you can define how many days of usage history should be retained. Rows older than the configured retention period are automatically removed.