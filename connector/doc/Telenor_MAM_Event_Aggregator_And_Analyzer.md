---
uid: Connector_help_Telenor_MAM_Event_Aggregator_And_Analyzer
---

# Telenor MAM Event Aggregator And Analyzer

## About

The **Telenor MAM Event Aggregator and Analyzer** connector queries an OpenSearch database for MAM events and performance data offloaded from the TV platform. Because the raw data in OpenSearch is retained for only a short period, the connector aggregates it into DataMiner tables for long-term trending, analysis, and alerting.

It produces multiple aggregations, including error events (per device class, per device model, and per asset), MAM events per device class, ContentWise API usage, NPVR statistics, playback sessions, player statistics, and unique devices in use. Each aggregation has its own configurable aggregation period and retention window, and can be filtered per operator.

## Key Features

- **Broad set of aggregations**: Analyze error events, MAM events, ContentWise API usage, NPVR statistics, playback sessions, player statistics, and unique device usage from a single element.

- **Error statistics from offloaded data**: Analyze error trends over time and identify periods with elevated error counts, broken down by device class, device model, and asset.

- **Long-term retention**: Store short-lived OpenSearch data in DataMiner tables with a configurable retention period per aggregation.

- **Customizable aggregation periods**: Adjust each aggregation window independently to optimize resolution and system load.

- **Operator filtering**: Scope the data to all operators or to a specific operator (Norway or Sweden).

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Telenor_MAM_Event_Aggregator_And_Analyzer_Technical).
