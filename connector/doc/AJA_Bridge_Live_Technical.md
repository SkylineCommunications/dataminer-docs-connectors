---
uid: Connector_help_AJA_Bridge_Live_Technical
---

# About

BRIDGE LIVE is the broadcast quality, low latency turnkey system for REMI, Synchronous Multi-Channel Video Contribution, Remote Collaboration, Direct to Audience Streaming, and Multi Bit Rate/ Multi Format Delivery.

## Configuration

### Connections

#### HTTP Connection - Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination.]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]

### Initialization

The **Configuration** subpage contains the **Username** and **Password** fields. These fields are used to authenticate the user to the device. The **Username** and **Password** fields are mandatory.

### Redundancy

There is no redundancy defined.

## How to use

REST API is used to retrieve the device information. The connector can be used to retrieve the device information and monitor the device status.

The **Pipelines** page shows information about all available Pipelines. You can also Start and Stop Pipelines from this page.

Pipelines can edited from the **Inputs** and **Outputs** pages.

All sets to the device can be found on the **Pipeline Sets** page.