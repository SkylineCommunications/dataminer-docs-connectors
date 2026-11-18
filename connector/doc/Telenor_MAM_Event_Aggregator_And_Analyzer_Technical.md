---
uid: Connector_help_Telenor_MAM_Event_Aggregator_And_Analyzer_Technical
---

# Telenor MAM Event Aggregator And Analyzer

## About

In the Telenor DMS, the **Telenor MAM Event Aggregator and Analyzer** element queries an OpenSearch database for MAM events and performance data offloaded from the TV platform, aggregates it, and stores the results in DataMiner tables.

Since the raw data in OpenSearch is retained for only 21 days, the primary purpose of this element is to aggregate and store the data for long-term analysis. It also enables alerting based on error counts.

The element performs several independent aggregations, each with its own configurable aggregation period and retention window:

- **Error events** grouped by device class, device model, and asset.
- **Total MAM errors** (playback errors, notifications shown, and playback warnings) grouped by device class, for the last 15 minutes, hour, and day.
- **MAM events** grouped by device class.
- **ContentWise API usage** (recommendation service performance).
- **NPVR statistics**.
- **Playback sessions** grouped by category and model.
- **OTT Live channel statistics** grouped by channel and device class, for the last 15 minutes, hour, and day.
- **Player statistics**.
- **Unique devices in use** and **unique devices per firmware version**.
- **App system events**.
- **Connection link distribution** per device class, aggregated from the Telenor EPM Collector elements in the DMS.

All aggregations can be scoped to a specific operator or to all operators combined.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

### General

On the **General** page, you can:

- View statistics from the latest aggregation run, including the duration and end time of each aggregation type.
- Select the **Operator** for which the element aggregates data: **All**, **Norway**, or **Sweden**.
- Configure, for each aggregation type, the **aggregation period** (in minutes) and, where applicable, the **retention period** (in days), which determines how long aggregated data is kept.
- Enable or disable the individual aggregation processes (for example, unique devices, app system events, NPVR statistics, player stats, and playback session aggregations).

### Aggregation Period

Each aggregation period is configurable, except for the **Total MAM Errors** and **Connection - Link** aggregations, which run every 15 minutes on a fixed internal timer.

The start and end times are calculated as follows:

- **End Time**:
  - Day: `current day`
  - Hour: `current hour`
  - Minutes: `floor(currentMinutes / aggregationPeriod) * aggregationPeriod`
- **Start Time**: `End Time - aggregationPeriod`

Each aggregation only collects new data since its last recorded end time, avoiding double counting, and automatically removes entries that fall outside the configured retention period.

### Data Tables

The aggregated data is displayed on several pages. The main ones are:

- **Errors Per Device Class**: The total number of errors during the aggregation period, grouped by error code and device class, together with the number of distinct devices that generated those errors. Hourly, daily, and history-window totals are maintained.

- **Errors Per Device Model**: The same error aggregation as above, but grouped by error code and device model. The device models to aggregate are configured in the **Device Models Configuration** table.

- **Errors Per Asset**: The total number of errors during the aggregation period, grouped by error code and asset ID (channel, Catch-Up event, or VoD asset), together with the asset name and the number of affected devices. Only the error codes listed in the **Error Code Per Asset Configuration** table are aggregated here.

- **MAM Events Per Device Class**: The total number of MAM events during the aggregation period, grouped by device class.

- **Total MAM Errors**: Per device class, the number of **Playback Errors**, **Notifications Shown**, and **Playback Warnings** events aggregated from the errors stream, together with the number of **Unique Devices** reporting these events and the **Total Events** count. Three tables are available, covering the last **15 minutes**, **1 hour**, and **1 day**. The values are refreshed every 15 minutes and trending is enabled.

- **ContentWise API Usage**: Request counts by status (200/400/500), cache hit/miss counts, and response-time statistics (average, 95th and 99th percentile) for the ContentWise recommendation API, for each tenant and overall.

- **NPVR Statistics**: Aggregated network PVR statistics.

- **Playback Per Category** and **Playback Per Model**: Aggregated playback session statistics grouped by category and by device model.

- **Player Stats** and **OTT Live SO** pages: Player and streaming statistics broken down for each device platform (for example, STB, Smartphone, Tablet, PC Portal, Apple TV, Android TV, Chromecast).

- **OTT Live Playback Sessions**: Combined OTT Live channel statistics by **channel and device class**, with separate tables for the last **15 minutes**, **1 hour**, and **1 day**. Each table shows the number of devices **watching** the channel, together with average playback metrics such as **SPI**, **Stalled**, **Profile Change**, **Bit Rate**, **Setup Error Events**, **Playback Error Events**, **Time to Video Start**, and **DRM Error Events**.

- **Connection - Link**: For every device class, link type, and country, the number of devices with that link type active and the percentage this represents within the device class. Unlike the other aggregations, this data is not retrieved from OpenSearch: every 15 minutes, the connector reads the Device table of the **Telenor EPM Collector** elements in the DMS through SLNet. Which collector elements are queried depends on the configured **Operator**: *All* queries every collector, while *Norway* or *Sweden* only queries the collectors of the matching country.

- **Unique Devices in Use** and **Unique Devices FW Version**: Counts of distinct devices actively using the service over several time windows, grouped by operator, device class, device model, platform, and firmware version.

- **App System Event**: Aggregated application system events.

### Configuration Tables

Two tables let you control which items are aggregated at the detailed level:

- **Error Code Per Asset Configuration**: The list of error codes to aggregate in the **Errors Per Asset** view. Use the context menu to add or remove error codes.

- **Device Models Configuration**: The list of device models to aggregate in the **Errors Per Device Model** view. Use the context menu to add or remove device models.
