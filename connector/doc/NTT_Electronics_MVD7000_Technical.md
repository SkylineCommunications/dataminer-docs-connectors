---
uid: Connector_help_NTT_Electronics_MVD7000_Technical
---

# NTT Electronics MVD7000 Technical

## About

The **NTT Electronics MVD7000** is a high-performance HEVC IP decoder designed for professional broadcast applications, offering H.265/HEVC and H.264/AVC decoding with ultra-low latency.
It supports dual-stream decoding, embedded audio, and robust IP transmission with FEC and ARQ for reliability. Its compact 1U half-rack design makes it ideal for space-efficient deployments.

The **NTT Electronics MVD7000** connector is used to monitor and configure the **MVD7000** decoder from **NTT Electronics**.

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

This page displays general information about the device as well as the **Last Event** data.
There are multiple page-button containing data about the **Device State** and **Device Interfaces** information.

> [!NOTE]
> On the sub-page **PPPoE 1** parameter **PPPoE1 Gateway** shows as **Not Initialized** this a device issues.
> The value is present on the web interface but not available via SNMP (OID exists but the device is not sending data for that parameter).

### Decode Status

This page contains the **Decode Status** parameters, which displays the status of the decoder parameters.

### PID

**PID** page contains overview of all the PID information in regards to the device.

### Output Status

This page contains the **Output Status** parameters, containing all the relevant output status values.

### Streaming Status

**Streaming Status** page displays all the relevant parameters to the streaming status of the device.

### Receive Information

This page contains the **Receive Information** parameters, which displays the status of the receive information.

### Packet Counters

**Packet Counters** page displays all the relevant parameters to the packet counters of the device.
As well as button which clears the packet counters data.

### Streaming Common

The page contains common parameters which apply to the available streams.

### IP1 Receive, IP2 Receive

These pages contain all the available configuration parameters for the IP1 and IP2 receive information.

### Decode

The **Decode** page contains all the relevant information regarding the decoding of the device. Such data being the **Input/Output**, **Superimpose**, **Decode** and **PID** parameters which the user is able to configure.

### Control, Data1 and Data2 Interfaces

The interfaces pages contain all the data in regards to the Control, Data 1 and Data 2 device interfaces. The user has the ability to alter the settings of the device interfaces.

### System Settings

This page allows you to view and configure the system settings. Such as the device **Time Zone**, **Date**, "**Time** and **NTP** data.

### Preferences

This page allows you to view and configure the preset information.

### Traps

The traps page contains a table containing all the relevant information regarding the traps that the device has sent.
As well it contains a page buttons to the following sub-pages: **Last Trap Data** and **Clean up Configuration**.

**Last Trap Data** displays the last trap data received from the device.
**Clean up Configuration** contains parameters that will activate automatic cleanup of the traps table.