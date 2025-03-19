---
uid: Connector_help_Grass_Valley_AMPP_Virtual_Crosspoint_Application_Technical
---

# Grass Valley AMPP Virtual Crosspoint Application

## About

The Virtual Crosspoint is an application connector defined for the Grass Valley AMPP (Agile Media Processing Platform) solution, designed to show the status and allow the configuration of the workloads added to a fabric in AMPP. It depends on InterApp messages from the Grass Valley AMPP Manager.

An HTTP connection is used to send commands to the Grass Valley AMPP platform, and InterApp messages are used to communicate with the Grass Valley AMPP Manager that receives all the data from the platform.

## Configuration

### Connections

#### HTTP Connection - AMPP

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

After the element is created, the element needs to be linked to the desired Virtual Crosspoint workload(s) in the Grass Valley AMPP Manager. To do so:

1. Navigate to the **Workloads** page of the **Grass Valley AMPP Manager element**.

1. Search for the desired Virtual Crosspoint workload(s) in the **Workloads table**.

1. In the **element** column of the **Workloads table**, specify the **name** of the Virtual crosspoint element.

Based on the state of the workload(s) in the element, different commands can be sent, e.g. start, stop, get state, etc. For more details, refer to the [Manager page](xref:Connector_help_Grass_Valley_AMPP_Manager_Technical).

## How to use

The connector is mostly self-reliant. It receives updates from the manager for the workload(s) it is currently monitoring.

In the Crosspoint Overview table at the bottom of the General page, the following settings are available:

- **Change Producer**: Allows you to **change the producer** of the Virtual Crosspoint by specifying the desired producer in the **Routed Source column**.
- **Clear Producer**: Allows you to clear the producer by clicking the **Clear Producer button**.
