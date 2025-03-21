---
uid: Connector_help_AJA_Bridge_Live_Technical
---

# AJA Bridge Live

## About

BRIDGE LIVE is the broadcast-quality, low-latency turnkey system for REMI, synchronous multi-channel video contribution, remote collaboration, direct-to-audience streaming, and multi bit rate/multi format delivery.

## Configuration

### Connections

#### HTTP Connection - Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

The **Configuration** subpage contains the **Username** and **Password** fields. These fields are used to authenticate the user to the device. These fields must be filled in for the connector to be able to retrieve information.

## How to use

REST API is used to retrieve the device information. The connector can be used to retrieve the device information and monitor the device status.

The **Pipelines** page shows information about all available pipelines. You can also start and stop pipelines from this page.

Pipelines can be edited from the **Inputs** and **Outputs** pages.

All sets to the device can be found on the **Pipeline Sets** page.
