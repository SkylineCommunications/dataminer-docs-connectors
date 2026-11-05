---
uid: Connector_help_OpenSearch_Cluster_Monitor
---

# OpenSearch Cluster Monitor

## About

The **OpenSearch Cluster Monitor** connector monitors the health of an OpenSearch or Elasticsearch cluster by performing HTTP queries against one of the cluster nodes.

This connector retrieves health metrics from the cluster REST API, covering cluster and node statistics, index and shard health, JVM performance, file system usage, circuit breakers, thread pools, and TLS certificate information.

## Key Features

- **Cluster health overview**: Monitors cluster status, shard distribution, and pending tasks.
- **Node-level statistics**: Collects metrics per node for CPU, memory, JVM, file system, transport, and thread pools.
- **Index and shard health**: Provides health status at both the index and shard level, with a tree view for quick navigation.
- **TLS certificate monitoring**: Retrieves and displays TLS certificates from the cluster, supporting both mTLS and handshake-based inspection.
- **Node settings**: Exposes all node-level configuration settings retrieved directly from the cluster.

## Use Cases

### Monitoring Cluster Health

Use this connector to keep track of the overall cluster status, including the number of active, relocating, and unassigned shards, and the percentage of active shards across the cluster.

### Tracking Node Performance

Monitor resource usage per node (CPU, heap, RAM), JVM garbage collection behavior, thread pool saturation, and file system utilization to identify bottlenecks before they impact production workloads.

### TLS Certificate Expiry Monitoring

Configure the connector with CA and client certificate paths to retrieve detailed certificate information, including subject, issuer, and expiration date, enabling proactive certificate lifecycle management.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [Technical help page](xref:Connector_help_OpenSearch_Cluster_Monitor_Technical).
