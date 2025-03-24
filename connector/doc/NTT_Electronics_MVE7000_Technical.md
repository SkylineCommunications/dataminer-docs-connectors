---
uid: Connector_help_NTT_Electronics_MVE7000_Technical
---

# NTT Electronics MVE7000 Technical

This connector is used to monitor and configure the **MVE7000** Encoder from **NTT Electronics**.

## About

The **NTT Electronics MVE7000** is a high-performance HEVC IP encoder designed for ultra-low latency HD video transmission. 
It supports H.265/HEVC encoding, multiple input interfaces (3G-SDI, HDMI), and features seamless IP transmission with FEC and ARQ for reliability.

The **NTT Electronics MVE7000** connector is used to monitor and configure the **MVE7000** Encoder from **NTT Electronics**.

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

### Encode Input Status

This page contains the **Encode Input Status** parameters, which displays the status of the encoder input parameters.

### Encode Status

**Encode Status** page contains all the relevant parameters to the encoding status of the device.

### Streaming Status

**Streaming Status** page displays all the relevant parameters to the streaming status of the device.

### Input/Output

This page contains all the relevant configuration parameters for the input and output settings of the device.

### Superimpose

This page contains all the relevant configuration parameters for the superimpose settings of the device.

### Video

This page contains all the relevant configuration parameters for the video settings of the device.

### Audio

This page contains all the relevant configuration parameters for the audio settings of the device.

### PID

**PID** page contains all the PID information in regards to the device.

### TS MUX

This page contains all the relevant configuration parameters for the TS MUX settings of the device.

### Streaming Common

The page contains common parameters which apply to the available streams.

### Stream 1, Stream 2, Stream 3, Stream 4

These pages contain all the available configuration parameters for the Stream 1, Stream 2, Stream 3 and Stream 4 settings.

### Control, Data1 and Data2 Interfaces

The interfaces pages contain all the data in regards to the control, data1 and data2 device interfaces. The user has the ability to alter the settings of the device interfaces.

### System Settings

This page allows you to view and configure the system settings. Such as the device **Time Zone**, **Date**, "**Time** and **NTP** data.

### Preferences

This page allows you to view and configure the preset information.

### Traps

The traps page contains a table containing all the relevant information regarding the traps that the device has sent.
As well it contains a page buttons to the following sub-pages: **Last Trap Data** and **Clean up Configuration**.

**Last Trap Data** displays the last trap data received from the device.
**Clean up Configuration** contains parameters that will activate automatic cleanup of the traps table.