---
uid: Connector_help_TMD_MediaFlex_UMS
---

# TMD MediaFlex UMS

The TMD MediaFlex UMS connector integrates the Mediaflex Unified Media Services Cloud platform into DataMiner. This platform pushes the list of scheduled events to the DataMiner connector, which in turn will display the events in a table and trigger an Automation script, automatically or manually, to create the corresponding SRM bookings.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |
| 2.0.0.x              | YLE specific version  | -       | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |
| 2.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 2.0.0.x   | No                  | Yes                     | [SLC-S-TMD-MediaFlex-UMS-ConnectorAPI](https://github.com/SkylineCommunications/SLC-S-TMD-MediaFlex-UMS-ConnectorAPI) | -                       |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

### Initialization

#### 1.0.0.X

On the **Configuration** page, fill in **sites** that the bookings supports in the Sites table

##### 2.0.0.X

On the **Configuration** page you will need to configure the web service hosted by the element. This web service is used to receive notifications coming from MediaFlex.

## How to use

### 1.0.0.X

Bookings and all their relevant information are located on the **General** page. The connector adds entries by parsing an **HTTP** response.

You can find additional settings for the Bookings table on the **Configuration** page. Site names should be configured before any booking are created.

### 2.0.0.X

Notifications coming from MediaFlex and sent to the web service hosted by the element are placed in the File Status Updates table on the **General** page.

Using the linked ConnectorAPI NuGet package you are able to send metadata workflow updates to MediaFlex. 
