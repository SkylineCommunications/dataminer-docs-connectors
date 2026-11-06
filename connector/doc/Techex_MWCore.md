---
uid: Connector_help_Techex_MWCore
description: "Monitor and configure Techex TXCore clusters, TXEdges, streams, sources, outputs, and telemetry in DataMiner, with optional device DVEs."
---

# Techex MWCore

## About

**Techex TXCore** (formerly known as MWCore) is a platform that manages TXEdge (formerly MWEdge) devices and captures telemetry data for real-time monitoring of live video transport.

The **Techex MWCore** connector integrates the TXCore platform with DataMiner. Through the TXCore REST API, it monitors and configures cluster members, devices, channels, TXEdges, streams, sources, and outputs. In addition, a dedicated statistics connection with each TXCore node delivers real-time telemetry for sources and outputs, including ETR 290 statistics.

## Key Features

- **Cluster Infrastructure Monitoring**: Monitor the health of every node in the TXCore cluster, including CPU, memory, and disk usage, as well as the number of devices and TXEdges connected to each node.

- **TXEdge Monitoring**: Track the state of all TXEdges or a filtered subset, including addresses, licenses, number of streams, and bandwidth usage.

- **Real-Time Telemetry**: Receive bit rates, missing packets, source and output states, and ETR 290 messages asynchronously through the statistics connection, so that alarms and trends reflect the live situation.

- **Stream, Source, and Output Configuration**: Add, edit, and delete channels, streams, sources, and outputs directly from DataMiner, and clear statistics for a selected stream, source, or output.

- **Connection Redundancy**: Specify additional TXCore nodes in the Connections table so that DataMiner automatically fails over when the primary node becomes unavailable.

- **Automation and SRM Integration**: Use the InterApp library and the SRM resource tables to orchestrate streams, sources, outputs, and ports from Automation scripts and SRM solutions.

## Use Cases

### Centralized Monitoring of Distributed TXCore Clusters

**Challenge**: A TXCore deployment typically consists of multiple cluster nodes and a large number of TXEdges spread across locations. Checking node health, edge state, and license usage in separate TXCore interfaces slows down incident response and makes it difficult to maintain an overall view.

**Solution**: The connector consolidates all cluster members, devices, channels, and TXEdges in a single DataMiner element. Node health, edge state, and connectivity between DataMiner and TXCore are monitored continuously, and DataMiner automatically switches to another cluster node if the primary node becomes unavailable.

**Benefit**: Faster detection and resolution of issues, and a reliable overall view of the TXCore infrastructure from one platform.

### Real-Time Quality Monitoring of Live Streams

**Challenge**: Polling-based monitoring cannot keep up with the frequency at which stream quality changes. Operators need immediate visibility into bit rates, packet loss, and ETR 290 errors to react before viewers are affected.

**Solution**: Each TXCore node pushes telemetry for sources and outputs to DataMiner over a dedicated statistics connection. The connector exposes this data in statistics tables, source and output state tables, and an ETR 290 table, where alarm templates and trending can be applied.

**Benefit**: Immediate alerting on stream quality degradation and historical trend data for root cause analysis.

### Orchestrating Stream Configuration from DataMiner

**Challenge**: Configuring streams, sources, and outputs manually in the TXCore user interface for every event or workflow change is time-consuming and error-prone, especially when it must be coordinated with other systems.

**Solution**: The connector allows you to create, update, and delete channels, streams, sources, and outputs from DataMiner, either interactively or through the InterApp library and SRM resource tables. This makes TXCore configuration part of automated DataMiner workflows.

**Benefit**: Consistent and repeatable configuration, reduced manual effort, and end-to-end orchestration of video workflows alongside other DataMiner-managed systems.

For a real-world example, see the [Mastering TXCore orchestration with DataMiner](https://community.dataminer.services/use-case/mastering-tx-core-orchestration-with-dataminer/) use case on DataMiner Dojo.

## Technical Reference

### Prerequisites

- **TXCore REST API access**: The DataMiner Agent must be able to reach the TXCore REST API over HTTPS (default port *443*), and a TXCore user account is needed for authentication.

- **Client certificate**: A .pfx client certificate is required to establish the statistics connection with each TXCore node.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Techex_MWCore_Technical).