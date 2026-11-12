---
uid: Connector_help_Zixi_Zen_Master
description: "Monitor and manage Zixi Zen Master live video networks in DataMiner, tracking broadcasters, feeders, receivers, sources, channels, targets, and events."
---

# Zixi Zen Master

## About

Zixi Zen Master is the central control point for a Zixi live video delivery network. This connector brings the health and configuration of that network into DataMiner, so operators can follow every video stream, and the equipment carrying it, from a single place.

## Key Features

- **One view of your entire video delivery network**: See broadcasters, feeders, receivers, sources, channels, and targets side by side, instead of switching between tools.

- **Complete visibility of your streams**: Follow each stream from its source, through the channels that carry it, to the targets that receive it.

- **Built-in event tracking**: Keep a history of events reported by Zen Master, so you can quickly understand what happened and when.

## Use Case: Monitoring Live Video Delivery from One Dashboard

**Challenge**: Live video delivery relies on many connected components. Operators often have to check each one separately to find out where a problem occurs.

**Solution**: The connector collects the status of all broadcasters, feeders, receivers, sources, channels, and targets in DataMiner, where they can be shown on dashboards and in alarm views.

**Benefit**: Operators spot issues faster, find the affected part of the delivery chain sooner, and reduce the time that viewers are impacted.

## Technical Reference

### Prerequisites

- **A Zen Master account** is needed for the connector to access the system. Either an API key or a username and password can be used.

### Connection

When you create a DataMiner element with this connector, configure the HTTP connection as follows:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

Before the API can be polled, you need to specify the **Username** and **Password** on the **Configuration** page. Click the **Connect** button to trigger the connection setup.
