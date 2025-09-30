---
uid: Connector_help_NTT_Electronics_HC32000E_Technical
---

# NTT Electronics HC32000E

## About

With this connector, it is possible to monitor the hardware and performance status of an HC32000E device and to change the configuration of some of its parameters. The connector uses an **SNMP connection** to retrieve data from the device and to set parameters on it.

## Configuration

### Connections

#### SNMP Main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General

This page displays **System Information**, such as the system name and version, **Alarm Status** information, and **Device Status** information, such as the device temperatures, fan status, etc.

### Alarms

This page displays the **Alarm Table**, which lists the active alarms of the device.

### Status

This page displays detailed information regarding the device network, input signal, and encoding status.

The page contains page buttons to the following subpages:

- **Status - IP**: Displays parameters regarding **TX 1** and **TX 2** metrics (Bitrate, Count Resend Packet, Delay Time, etc.).
- **Status - Network 1** and **Status - Network 2**: These subpages display parameters related to the network interfaces.
- **Status - Input**: Displays parameters related to the input signal for this device (SDI 1, SDI 2, SDI 3, and SDI 4).
- **Status - Encode**: Displays parameters related to the Video Encoder Status and Audio Encoder Status.
- **Status - Ancillary**: Display parameters related to the ancillary status.

### Configuration - Input

On this page, you can navigate to the configuration parameters of **Video Input** (4K Division, Black Screen HD SDI, and Frame Sync), **Audio Input** and **Audio Gain** parameters.

### Configuration - Output

This page allows you to configure parameters related to the **Output** of the device (ASI Format) and to the **Output IP** (Data MPEG2 TS Format, Packet Density, Copy Cast, and Output IP Data Table).

### Configuration - Encode

This page contains encode configuration parameters (Stream Mode and Stream TS).

The page contains page buttons to the following subpages:

- **Encode Stream - TS Ancillary**: Displays the Encode Stream Ancillary Table.
- **Encode Stream - TS Audio**: Displays the Encode Stream Audio Table.
- **Encode Stream - TS Program**: Displays the Stream Program Table.
- **Encode Stream - TS TS1**: Displays the Stream TS Table.
- **Encode - BISS**: Displays the BISS Encode Table.
- **Encode - Ancillary**: Displays the Ancillary 4K Source Table, Encode Ancillary Table, User Selection 1 Table, and User Selection 2 Table.
- **Encode - Audio**: Displays the Encode Audio Table, Encode Audio AAC Table, Audio Mapping Table, and Audio SMPTE302M Table, as well as the Audio Mapping Mode and Audio ARIB B39 parameters.
- **Encode - Video**: Displays the Video Format, Latency, Priority, Low Delay Refresh Cycle, Custom Low, and Encode Video Tables.
- **Encode - TCP**: Displays the TCP Control Interface and Port Tables.
- **Encode - Multi Stream**: Displays the Multi Stream TS and Program Audio Tables.
- **Encode - Multi Stream**: Displays the Multi Video Table.

### Presets

This page displays parameters related to presets, such as **Active Preset** and **Startup Preset**, as well as the **Preset List**, where you can configure the different available presets.

### Network

This page allows you to configure the **Network Host Name** and the **Network 1** and **Network 2** ports.

There are several page buttons available, which allow you to configure:

- **Network SNMP** ports, community strings and SNMP traps
- The **Network Web UI** port.
- **Network Monitoring** target parameters.
- **Network Syslog** IP parameters.
- **Network PPoE** session parameters.
- **Network Firewall** filter parameters.
- **Network Data** parameters, such as DHCP, IPv4/IPv6 addresses, subnet masks, Gateway, etc.

### Event Log

On this page, the **Event Customize Table** allows you to configure a particular level for each specific event ID.

### Miscellaneous

On this page, several other parameters can be configured: **Buzzer Volume**, **Front Panel Customize** and **User Text**, **NTP Server Name**, **Time Zone**, **Time Sync**, **Date** and **Time**, etc.

There are also three action buttons: **Clear Alarms**, **Reboot System**, and **Clear Packet Counter**.

### Web Interface

This page contains the web interface for the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
