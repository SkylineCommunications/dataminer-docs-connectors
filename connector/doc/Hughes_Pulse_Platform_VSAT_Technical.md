---
uid: Connector_help_Hughes_Pulse_Platform_VSAT_Technical
---

# Hughes Pulse Platform VSAT

## About

The Hughes Pulse Platform VSAT connector integrates remote terminal data from the Hughes Pulse API into DataMiner. It retrieves device status, performance metrics (ICMP, signal strength, throughput), and configuration details by polling HTTP endpoints.

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

| HTTP Verb | Endpoint                                                  | Category | Timer   |
|-----------|-----------------------------------------------------------|----------|---------|
| GET       | `assets/device?san=*`                                     | Remotes  | 30 min  |
| GET       | `assets/device?san=*&fields=["name","state"]`             | Remotes  | 5 min   |
| POST      | `telemetry/metrics?metric_name=icmp`                      | Metrics  | 5 min   |
| POST      | `telemetry/metrics?metric_name=signalStrength`            | Metrics  | 5 min   |
| POST      | `telemetry/metrics?metric_name=throughput`                | Metrics  | 5 min   |

The following configuration options are available for each entry:

- Polling interval
- Enable/disable polling
- Display last API response
- Manual **Poll** button
- HTTP verb (GET or POST)
- Custom POST body content

> [!NOTE]
> You can add additional endpoints for testing, categorized as *N/A*. However, be careful when editing the automatically added endpoints, as they populate the **Remotes** and **Metrics** tables:
>
> - The default `pagesize` in the body of metric endpoints is `500`. If the number of devices exceeds this, you may need to increase it.
> - You can apply filters to the POST body to reduce the number of returned remotes.
> - **Do not change the *Category*** of the default endpoints. Changing it to anything other than *Remotes* or *Metrics* will keep the corresponding table from being populated. If this does happen, remove the affected row from the table and restart the element. This will recreate the row with the default values.

#### Default Metric POST Body

Below is the default POST body used for the metric endpoints (`icmp`, `signalStrength`, `throughput`):

```json
{
    "devices": "{{devices}}",
    "filter": [],
    "time_choice": "1 day",
    "offset": 0,
    "pagesize": 500,
    "sort": "",
    "sortOrder": "asc"
}
```

> [!NOTE]
>
> - `{{devices}}` is replaced at runtime with the list of device IDs from the Remotes Overview table.
> - You can adjust `pagesize`, `filter`, or `time_choice` to optimize performance.
> - Ensure your changes conform to the API's format to avoid 500 errors.

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

#### Collector Setup Page

This page contains settings for managing entities, including options for enabling automatic entity removal and configuring the removal period. This feature clears entries in the tables that have not been updated within the specified period.
