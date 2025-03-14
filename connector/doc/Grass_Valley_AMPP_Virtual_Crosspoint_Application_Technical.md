---
uid: Connector_help_Grass_Valley_AMPP_Virtual_Crosspoint_Application_Technical
---

# Grass Valley AMPP Virtual Crosspoint Application

The Virtual Crosspoint is an application connector defined for the Grass Valley AMPP (Agile Media Processing Platform) solution, designed to show the status and allow the configuration of the workloads added to a fabric in AMPP. It depends on InterApp messages from the Grass Valley AMPP Manager.

## About
A HTTP connection is used to send commands to the Grass Valley AMPP platform and InterApp messages are used to communicate with the Grass Valley AMPP Manager that receives all the data from the platform.

## Configuration

### Connections

#### HTTP Connection - AMPP

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *443*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]


### Initialization

After the element is created, the element needs to be linked to the desired Virtual Crosspoint workload(s) in the Grass Valley AMPP Manager. To linked the element in the Grass Valley AMPP Mananger,
 - Navigate to the **Workloads** page in the **Grass Valley AMPP Manager element**.
 - Search for the desired Virtual Crosspoint workload(s) in the **Workloads table**.
 - Enter the **name of the Virtual crosspoint element** that will be linked to the desire workload(s) **in the element column in the Workloads table**.
 - Based on the state of the of the workload(s) in the element, there are options that can be perform. for e.g. start, stop, get state, etc. **refer to the Manager help page for more details**.

## How to use

The connector is mostly self reliant, the connector receives updates from the manager for the workload(s) it is currently monitoring. There are two configuration in the Crosspoint Overview table at the bottom of the general page. The two configuration are as followed

- **Change Producer**: This allow the user to **change the producer** of the Virtual Crosspoint by entering the desired producer **in the Routed Source column**.
- **Clear Producer**: This allow the user to clear the producer **by clicking the Clear Producer button**.