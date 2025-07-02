---
uid: Connector_help_Telenor_MAM_Event_Aggregator_And_Analyzer_Technical
---

# Telenor MAM Event Aggregator And Analyzer

## About

In the Telenor DMS, the **Telenor MAM Event Aggregator and Analyzer** element queries an OpenSearch database for aggregated MAM error events offloaded by the system. Aggregations are performed by *Device Class Type* and *Asset ID*.

Since the raw data in OpenSearch is retained for only 21 days, the primary purpose of this element is to aggregate and store the data for long-term analysis. It also enables alerting based on error counts.

Aggregated data is stored in two tables:

- **Error Events Per Device Type**
- **Error Events Per Asset ID**

These tables support further analysis and reporting.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to Use

On the **General** page, you can:

- View statistics from the latest aggregation.
- Set the aggregation period in minutes.

### Aggregation Period

The aggregation period is configurable. The start and end times are calculated as follows:

- **End Time**:
  - Day: `current day`
  - Hour: `current hour`
  - Minutes: `floor(currentMinutes / aggregationPeriod) * aggregationPeriod`
- **Start Time**: `End Time - aggregationPeriod`

### Data Tables

Aggregated data is displayed in two pages:

- **Errors Per Device Type**
- **Errors Per Asset**

These pages contain the following columns:

#### Error Events Per Device Type

- **Events Count**: Total number of errors during the aggregation period, grouped by Error Code and Device Class.
- **Devices Count**: Number of distinct devices that generated errors during the aggregation period.

#### Error Events Per Asset ID

- **Events Count**: Total number of errors during the aggregation period, grouped by Error Code and Asset ID.


