---
uid: Connector_help_Haivision_Media_Gateway
---

# Haivision Media Gateway

The HTTP Rest API protocol connects to the Haivision Media Gateway to gather device and route statistics. The Haivision Media Gateway is a highly scalable broadcast solution for secure routing of live video streams across different types of IP networks.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [Obsolete] | Initial version. | - | - |
| 1.0.1.x [Obsolete] | Added support for all source and destination protocol types. | 1.0.0.1 | Removed SRT from Sources and Destinations tables to improve compatibility with other protocol types. This can affect DataMiner filters, Automation scripts, Visio drawings, reports, dashboards, and web API. |
| 1.0.2.x [Obsolete] | Complete revision of the connector: <br>- Fix for session creation/deletion. <br>- Added system metrics information. <br>- Possibility to start/stop routes and destinations. <br>- Possibility to add SRT/UDP/RTP/RTSP/RTMP routes. <br>- Possibility to add SRT/UDP/RTP/HLS destinations. | 1.0.1.x | - |
| 1.0.3.x [Obsolete] | Changed indexes and display keys for Source Statistics and Destination Statistics tables to allow multiple connection rows for each input. | 1.0.2.x | All data in the tables will be affected, as well as alarm templates, trend templates, and visual overviews. |
| 1.0.4.x [Obsolete]  | Changed indexes and display keys for Route, Source, and Destination tables to keep them unique. | 1.0.3.x | All data in the tables will be affected, as well as alarm templates, trend templates, and visual overviews. |
| 1.0.5.x [SLC Main]  | Modification of display keys and indexes to enable a format that will accommodate all possible data in tables. Required features are taken from all previous versions. | 1.0.5.1 | All data in the tables will be affected, as well as alarm templates, trend templates, and visual overviews. The addition of a Unicode tag will cause the element data and trending information in the database to be entirely removed. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 5.5.210518.1712        |
| 1.0.1.x   | 5.5.210518.1712        |
| 1.0.2.x   | 5.5.210518.1712        |
| 1.0.3.x   | 5.5.210518.1712        |
| 1.0.4.x   | 5.5.210518.1712        |
| 1.0.5.x   | 5.5.210518.1712        |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | No                  | Yes                     | -                     | -                       |
| 1.0.3.x   | No                  | Yes                     | -                     | -                       |
| 1.0.4.x   | No                  | Yes                     | -                     | -                       |
| 1.0.5.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

Once the element has been started, enter the **Username** and **Password** on the **General** page to ensure that the session is started appropriately.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

Once the authentication parameters have been set, the **route** information will be polled. After this, the **sources and destinations** will be polled and placed into the corresponding tables.

A tree view of the device structure can be viewed on the **Overview** page.
