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

This connector uses an HTTP connection to communicate directly with AMPP and push configuration commands. The URL is set by any AMPP Manager that utilizes this element to manage the specific visualization and configuration of the AMPP Application type. To create an element, it is necessary to enter a URL; in this case, you can use the value *http://localhost*.

HTTP CONNECTION:

- **IP address/host**: *http://localhost*.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Element Configuration

Once the application element is created, it must be linked to the desired Virtual Crosspoint workload(s) in any Grass Valley Manager. To accomplish this:

1. Annotate the name of the Virtual Crosspoint Application element.
2. Open the existing AMPP Manager and filter the Workloads table by the application name "*Virtual Crosspoint*"
3. Select a desired workload from the filtered list.
4. Click on the "*Refresh State on Restart*" column to configure the manager to receive notifications of the intended workload.
5. In the "*Element*" column, enter the name of the target application element noted in step 1.
6. The manager should present the "*Element Status (workloads)*" column as active, indicating that the target application element was found available in the system.
7. Press the "*Get State*" button to retrieve and forward the current configuration to the target application element. Confirm that the workload is visualized in the target with its current state.
8. To configure additional workloads for the target application, repeat the process starting from step 2.

> [!NOTE]
> Occasionally, it is necessary to restart the AMPP Manager to force a reconfiguration of the application element. Do this if you notice that the target element times out for a long period.

## How to use

The connector is mostly self-reliant. It receives updates from the manager for the workload(s) it is currently monitoring.

In the Crosspoint Overview table at the bottom of the General page, the following settings are available:

- **Change Producer**: Allows you to **change the producer** of the Virtual Crosspoint by specifying the desired producer in the **Routed Source column**.
- **Clear Producer**: Allows you to clear the producer by clicking the **Clear Producer button**.

