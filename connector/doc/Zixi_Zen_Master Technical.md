---
uid: Connector_help_Zixi_Zen_Master_Technical
---

# Zixi Zen Master

The Zixi Zen Master is a platform to monitor and control live video orchestration and telemetry. It provides a centralized overview of the Zixi devices.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

Before the API can be polled, you need to specify the **Username** and **Password** on the **Configuration** page. With the **Connect** button, you can enforce the connection setup.

### Redundancy

There is no redundancy defined.

## How to use

The first pages display **Broadcasters**, **Feeders**, and **Receivers** in a tree view.

The remaining pages (**Channels**, **Targets**, **Sources**, and **Events**) display information in a table.
