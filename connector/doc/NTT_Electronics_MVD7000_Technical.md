---
uid: Connector_help_NTT_Electronics_MVD7000_Technical
---

# NTT Electronics MVD7000 Technical

## About

The **NTT Electronics MVD7000** is a high-performance HEVC IP decoder designed for professional broadcast applications, offering H.265/HEVC and H.264/AVC decoding with ultra-low latency. It supports dual-stream decoding, embedded audio, and robust IP transmission with FEC and ARQ for reliability. Its compact 1U half-rack design makes it ideal for space-efficient deployments.

The **NTT Electronics MVD7000** connector is used to monitor and configure the MVD7000 decoder from NTT Electronics.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

This page displays general information about the device as well as the **Last Event** data. Via page buttons, you can access information about the **device state** and **device interfaces**.

> [!NOTE]
> On the **PPPoE 1** subpage, the parameter **PPPoE1 Gateway** will show as *Not Initialized* because of an issue in the device. This value is present on the web interface but not available via SNMP (the OID exists but the device is not sending data for that parameter).

### Decode Status

This page displays the status of the decoder parameters.

### PID

This page contains overview of all the PID information for the device.

### Output Status

This page contains all the relevant output status information.

### Streaming Status

This page displays all the relevant parameters for the streaming status of the device.

### Receive Information

This page displays the status of the receive information.

### Packet Counters

This page displays all the relevant parameters for the packet counters of the device. It also contains a button that allows you to clear the packet counters data.

### Streaming Common

The page contains common parameters that apply to the available streams.

### IP1 Receive and IP2 Receive

These pages contain all the available configuration parameters for the IP1 and IP2 receive information.

### Decode

This page contains all the relevant information regarding the decoding of the device. This includes the **Input/Output**, **Superimpose**, **Decode**, and **PID** parameters, which can be configured on the page.

### Control, Data1, and Data2 Interfaces

The interfaces pages contain all the data with regards to the control, data 1, and data 2 device interfaces. You can also alter the settings of the device interfaces.

### System Settings

This page allows you to view and configure the system settings, such as the device **Time Zone**, **Date**, **Time**, and **NTP** data.

### Preferences

This page allows you to view and configure the preset information.

### Traps

The traps page contains a table with all the relevant information regarding the traps that the device has sent.

It also contains page buttons to the following subpages:

- **Last Trap Data**: Displays the last trap data received from the device.
- **Clean up Configuration**: Contains parameters that will activate automatic cleanup of the traps table.
