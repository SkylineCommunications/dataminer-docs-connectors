---
uid: Connector_help_OpenSearch_Cluster_Monitor_Technical
---

# OpenSearch Cluster Monitor

## About

The **OpenSearch Cluster Monitor** connector monitors the health of an OpenSearch cluster. It performs HTTP queries against one of the cluster nodes to collect metrics on cluster health, node statistics, index operations, JVM performance, and more.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or hostname of a cluster node. Multiple nodes can be specified using semicolons (";"), e.g., `https://node1:9200;https://node2:9200`.
- **IP port**: The port of the OpenSearch or Elasticsearch node. Default: *9200*.

### Initialization

After element creation, go to the **Security** page to configure authentication and TLS settings:

- **User** and **Password**: Basic authentication credentials for the cluster.
- **CA Certificate Location**: Absolute file path to the root CA certificate (PEM format). Required for TLS chain validation.
- **Client Certificate CRT File Location**: Absolute file path to the client certificate (PEM format). Required for mutual TLS.
- **Client Certificate Key File Location**: Absolute file path to the client private key. Supports PKCS#1 (`RSA PRIVATE KEY`) and PKCS#8 (`PRIVATE KEY`) PEM formats. Required for mutual TLS.

If the certificate file paths are left empty, the connector retrieves TLS certificate information directly via TLS handshake inspection on port 9200.

## How to Use

### General

The General page displays the overall cluster health retrieved from `GET /_cluster/health?level=shards`:

- **Cluster Name**, **Cluster Status**, **Timed Out**.
- **Number of Nodes**, **Number of Data Nodes**.
- **Active Primary Shards**, **Active Shards**, **Relocating Shards**, **Initializing Shards**, **Unassigned Shards**, **Delayed Unassigned Shards**.
- **Number of Pending Tasks**, **Number of In-Flight Fetch Tasks**.
- **Task Max Waiting in Queue** (s), **Active Shards Percentage**.

### Cluster Stats - Nodes

This page contains general cluster node statistics, such as node communication statistics and JVM memory usage. A page button provides additional operating system and file system statistics aggregated at cluster level.

### Cluster Stats - Indices

This page contains general cluster index statistics, including shard and document storage counts. Page buttons lead to the following subpages:

- **Shards Health**: Shard-level health, including state and primary/replica designation.
- **Indices Health**: Index-level status, number of shards and replicas, and counts of active, relocating, initializing, and unassigned shards.
- **Indices - Cache/Segments**: Cache memory and segment statistics per index.

### Index Shards Level Overview

This page contains a tree view that provides an overview of the health status of cluster indices and their shards, based on the **Indices Health** and **Shards Health** tables.

### Index Overview

This page displays an overview of all cluster indices, including document count, stored size, health status, and other operational information, retrieved via the index stats API.

### Node Data

This page displays a per-node summary retrieved from `GET /_cat/nodes`:

- **Name**, **IP Address**.
- **Heap Usage (%)**, **RAM Usage (%)**, **CPU Load**.
- **Load Average**: 1-minute, 5-minute, and 15-minute averages.
- **Node Roles**: *Master*, *Ingest*, *Coordinating Only*, *Remote Cluster Client*, *Machine Learning*, *Cluster Manager*.

### Node Stats - General

This page displays general information per node retrieved from `GET /_nodes/stats`, including node ID, name, transport address, host, IP, timestamp, and custom attributes.

### Node Stats - Indices

This page displays tables with index operation statistics per node. Page buttons provide access to additional subpages:

- **Documents**: Total and deleted document counts.
- **Stored Indices**: Stored indices size.
- **Indexing**: Index/delete totals, current operations, failed counts, and throttle times.
- **Get**: Total and existing/missing GET operation counts and latencies.
- **Search**: Query and fetch totals, current operations, scroll and suggest statistics, and average query/fetch latency.
- **Merge**: Current and total merge counts, document counts, size, and throttle times.
- **Refresh**: Total refresh count, time, and listener count.
- **Flush**: Total flush count and time.
- **Warmers**: Current and total warmer counts and time.
- **Query Cache**: Memory size, hit/miss counts, cache size, and evictions.
- **Field Data & Completion**: Field data memory size and evictions, completion size.
- **Segments**: Segment count and memory usage per segment type (terms, stored fields, term vectors, norms, points, doc values).
- **Translog**: Operation count, size, uncommitted operations, and earliest last modified age.
- **Request Cache**: Memory size, evictions, hit/miss counts.
- **Recovery**: Current and throttle statistics.

### Node Stats - OS / Processes

This page displays per-node operating system statistics (CPU usage, memory, swap) and process statistics (open file descriptors, CPU time, memory).

### Node Stats - JVM

This page contains tables with JVM statistics per node:

- **JVM Memory Stats**: Heap used/max, non-heap used, and per-pool memory statistics.
- **JVM Threads & Classes**: Live and peak thread counts, class loading statistics.
- **JVM Garbage Collectors**: GC collection count and cumulative time per collector.
- **JVM Buffer Pools**: Count, capacity, and used memory for direct and mapped buffer pools.

### Node Stats - Thread Pool (including pages II & III)

This page contains per-node thread pool statistics for all thread pools, including active thread count, queue size, rejected task count, and completed task count. Statistics are spread across three pages because of the number of thread pool types.

### Node Stats - File System

This page contains tables with file system statistics per node:

- **File System Stats**: Aggregated available, free, and total disk space, plus I/O statistics.
- **File System Data**: Per-path available, free, and total disk space details.

### Node Stats - Communications

This page contains per-node network statistics:

- **HTTP Info**: Total opened and currently open HTTP connections.
- **Transport Statistics**: Transport-layer RX/TX byte counts and message counts.

### Node Stats - Circuit Breakers

This page contains per-node circuit breaker statistics for all breaker types (request, fielddata, in-flight requests, accounting, parent), including limit bytes, estimated size, overhead, and trip count.

### Node Stats - Other

This page contains tables with per-node statistics for auxiliary features:

- **Script Statistics**: Compilation count, cache evictions, and compilation limit triggered count.
- **Discovery Cluster State Queue**: Committed and pending cluster state update queue statistics.
- **Ingest Statistics**: Per-pipeline and per-processor ingest statistics, including count, time, failed count, and current count.

### Security

On this page, you can configure connection credentials and TLS settings:

- **User**, **Password**.
- **TLS State**: Indicates whether TLS is active (automatically detected during polling).
- **CA Certificate Location**, **Client Certificate CRT File Location**, **Client Certificate Key File Location**.

The **TLS Certificates** table displays certificates retrieved from the cluster via `GET /_plugins/_security/api/ssl/certs` (when mTLS is configured) or via TLS handshake inspection. It includes subject, issuer, thumbprint, validity period, and certificate type.

### Node Settings

This page displays a table with all node-level settings retrieved from `GET /_nodes/settings`. Each row represents a single setting and shows the node ID, setting name, and value.
