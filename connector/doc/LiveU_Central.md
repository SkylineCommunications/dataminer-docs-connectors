---
uid: Connector_help_LiveU_Central
---

# LiveU Central

LiveU Central is a management platform where live feeds can be monitored and managed. It gives a detailed view of the unit status, network interfaces and performance and can control live transmission attributes such as start/stop streaming, bandwidth, latency, etc.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [Obsolete]   | Initial version  | -            | -                 |
| 1.1.0.x [SLC Main]   | Support the new API endpoints and headers. <br> Minimum required DMA version: 10.1.11.0. | 1.0.0.11           | Need to fill in the new API Key parameter for the connector to work properly.                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | LUC Backend API 8.3    |
| 1.1.0.x   | Central Backend API 10.0    |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination (default: *lu-central.liveu.tv*).
- **IP port**: The IP port of the destination (default: *443*).

### Initialization

To initialize communication, you need to provide a username, password, APP ID and API Key on the **Connection** page.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The **General** page contains a tree view of all the units in the selected inventory.

You can select an inventory on the **Units** page. This page also contains the Units table, where the video stream of a unit can be started or stopped.
