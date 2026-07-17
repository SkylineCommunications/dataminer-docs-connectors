---
uid: Connector_help_Telenor_MAM_Event_Aggregator_And_Analyzer_Technical
---

# Telenor MAM Event Aggregator And Analyzer

## About

In the Telenor DMS, the **Telenor MAM Event Aggregator and Analyzer** element queries an OpenSearch database for MAM events and performance data offloaded from the TV platform, aggregates it, and stores the results in DataMiner tables.

Since the raw data in OpenSearch is retained for only 21 days, the primary purpose of this element is to aggregate and store the data for long-term analysis. It also enables alerting based on error counts.

The element performs several independent aggregations, each with its own configurable aggregation period and retention window:

- **Error events** grouped by device class, by device model, and by asset.
- **MAM events** grouped by device class.
- **ContentWise API usage** (recommendation service performance).
- **NPVR statistics**.
- **Playback sessions** (per category and per model).
- **Player statistics**.
- **Unique devices in use** and **unique devices per firmware version**.
- **App system events**.

All aggregations can be scoped to a specific operator or to all operators combined.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

### General

On the **General** page, you can:

- View statistics from the latest aggregation, including the last aggregation duration and the last aggregation end time of each aggregation type.
- Select the **Operator** the element aggregates for: **All**, **Norway**, or **Sweden**.
- Configure, per aggregation type, the **aggregation period** (in minutes) and, where applicable, the **retention period** (in days) that controls how long aggregated data is kept.
- Enable or disable the individual aggregation processes (for example, unique devices, app system events, NPVR statistics, player stats, and playback session aggregation).

### Aggregation Period

Each aggregation period is configurable. The start and end times are calculated as follows:

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

- **Contentwise API Usage**: Request counts by status (200/400/500), cache hit/miss counts, and response-time statistics (average, 95th and 99th percentile) for the ContentWise recommendation API, per tenant and overall.

- **NPVR Statistics**: Aggregated network PVR statistics.

- **Playback Per Category** and **Playback Per Model**: Aggregated playback session statistics grouped by category and by device model.

- **Player Stats** and **OTT Live SO** pages: Player and streaming statistics broken down per device platform (for example, STB, Smartphone, Tablet, PC Portal, Apple TV, Android TV, Chromecast).

- **Unique Devices in Use** and **Unique Devices FW Version**: Counts of distinct devices actively using the service over several time windows, grouped by operator, device class, device model, platform, and firmware version.

- **App System Event**: Aggregated application system events.

### Configuration Tables

Two tables let you control which items are aggregated at the detailed level:

- **Error Code Per Asset Configuration**: The list of error codes to aggregate in the **Errors Per Asset** view. Use the context menu to add or remove error codes.

- **Device Models Configuration**: The list of device models to aggregate in the **Errors Per Device Model** view. Use the context menu to add or remove device models.
