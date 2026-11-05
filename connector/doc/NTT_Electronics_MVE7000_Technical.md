---
uid: Connector_help_NTT_Electronics_MVE7000_Technical
---

# NTT Electronics MVE7000 Technical

## About

The **NTT Electronics MVE7000** is a high-performance HEVC IP encoder designed for ultra-low latency HD video transmission. It supports H.265/HEVC encoding, has multiple input interfaces (3G-SDI, HDMI), and features seamless IP transmission with FEC and ARQ for reliability.

The **NTT Electronics MVE7000** connector is used to monitor and configure the MVE7000 Encoder from NTT Electronics.

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

### Encode Input Status

This page displays the status of the encoder input parameters.

### Encode Status

This page contains all the relevant parameters for the encoding status of the device.

### Streaming Status

This page displays all the relevant parameters for the streaming status of the device.

### Input/Output

This page contains all the relevant configuration parameters for the input and output settings of the device.

### Superimpose

This page contains all the relevant configuration parameters for the superimpose settings of the device.

### Video

This page contains all the relevant configuration parameters for the video settings of the device.

### Audio

This page contains all the relevant configuration parameters for the audio settings of the device.

### PID

This page contains all the PID information for the device.

### TS MUX

This page contains all the relevant configuration parameters for the TS MUX settings of the device.

### Streaming Common

The page contains common parameters that apply to the available streams.

### Stream 1, Stream 2, Stream 3, and Stream 4

These pages contain all the available configuration parameters for the Stream 1, Stream 2, Stream 3, and Stream 4 settings.

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
