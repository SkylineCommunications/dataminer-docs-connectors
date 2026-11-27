---
uid: Connector_help_Apache_Cassandra_Cluster_Monitor_Technical
description: Technical details on configuring the Apache Cassandra Cluster Monitor connector, including its connection and Cassandra cluster credentials.
---

# Apache Cassandra Cluster Monitor

## About

The Apache Cassandra Cluster Monitor connector monitors an Apache Cassandra cluster, a distributed NoSQL database designed to handle large amounts of data. It retrieves information on the nodes, roles, tables, repair history, and more.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

> [!NOTE]
> For the **1.0.0.x** range only: Make sure *ApacheCassandraCluster.dll* and *System.Threading.Tasks.Dataflow.dll* are present on the DMA in the folder *C:\Skyline DataMiner\Files*.

### Initialization

When the element has been created, configure the connection to the Cassandra cluster:

1. Go to the **Connector Settings** page of the element.

2. Specify the **IP**, **Port**, **User Name**, and **Password** of the Cassandra cluster.

## How to Use

When the connection on the **Connector Settings** page has been configured, information from the Cassandra cluster will be retrieved and displayed in the element.

From range 1.0.1.x onwards, the connector also performs system checks on the cluster. From range 1.0.2.x onwards, you can launch the Cassandra Installer via a context menu in the element.

The connector supports Apache Cassandra 3.11 and 4.x (4.0 only for ranges prior to 1.0.2.x). With Cassandra 4.x, the connector also retrieves data from the following virtual tables: *clients*, *disk_usage*, *max_partition_size*, *settings*, and *tombstones_per_read*.