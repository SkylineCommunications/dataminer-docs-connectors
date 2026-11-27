---
uid: Connector_help_Apache_Cassandra_Cluster_Monitor
description: The Apache Cassandra Cluster Monitor connector monitors a Cassandra cluster, providing information on nodes, roles, tables, repair history, and more.
---

# Apache Cassandra Cluster Monitor

## About

Apache Cassandra is a NoSQL database designed to provide scalability, reliability, and availability with linear performance scaling. Cassandra databases are designed as a distributed system, aimed to handle big data efficiently.

This connector is designed to monitor a Cassandra cluster, providing useful information on nodes, roles, tables, repair history, and more.

## Key Features

- **Node monitoring**: Displays information on the nodes in the Cassandra cluster.
- **Role overview**: Lists the roles defined in the Cassandra cluster.
- **Table information**: Provides details on the cluster tables, including virtual tables such as clients, disk usage, maximum partition size, settings, and tombstones per read.
- **Repair history**: Shows the repair history of the cluster.
- **System checks**: Performs system checks on the Cassandra cluster.
- **Cassandra Installer integration**: Lets you launch the Cassandra Installer directly from a context menu in the element.

## Use Cases

### Centralized Cluster Visibility

**Challenge**: A Cassandra cluster is distributed across multiple nodes, which makes it difficult to get a clear overview of its overall state.

**Solution**: The connector retrieves node, role, and table information from the cluster and displays it in a single DataMiner element.

**Benefit**: You can follow up on the entire cluster from one place, using standard DataMiner alarm and trend capabilities.

### Following Up on Repairs

**Challenge**: Regular repairs are needed to keep data consistent across replicas, but verifying whether they were executed is time-consuming.

**Solution**: The connector displays the repair history of the cluster.

**Benefit**: You can quickly verify that repairs have run and detect gaps before they lead to data inconsistencies.

### Managing Cassandra Nodes

**Challenge**: Monitoring and setting up Cassandra nodes typically requires switching between different tools.

**Solution**: The connector provides a context menu to launch the Cassandra Installer directly from the element.

**Benefit**: You can monitor and manage your Cassandra setup from within DataMiner.

## Technical Reference

### Prerequisites
- **Apache Cassandra 3.11 or 4.x** is required. Version 4.x is needed to retrieve the virtual table data.
 
- **Cluster credentials** (IP, port, user name, and password) are needed to connect to the Cassandra cluster.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Apache_Cassandra_Cluster_Monitor_Technical).