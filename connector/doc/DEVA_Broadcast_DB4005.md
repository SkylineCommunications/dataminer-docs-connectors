---
uid: Connector_help_DEVA_Broadcast_DB4005
---

# DEVA Broadcast DB4005

The **DB4005** is a third-generation digital FM radio modulation analyzer.

The device monitors FM channels with a round-robin system. It keeps track of which channel is currently being monitored in order to poll the status parameters for that channel and then fill in the status data in a table.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.1.2117 (2023/02/17)  |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

This page displays the device info as well as alarm status parameters.

### General Settings

This page displays the following general device parameters: **Date**, **Time**, **Time Zone**, **Contrast**, **LED Brightness**, **Screen Saver**, **Panel Time**, and **Home Screen**.

### Channel Status

This page displays the Channel Status table, which contains the following parameters: **RF Status**, **MPX Status**, **MPX Power Status**, **Pilot Status**, **RDS Status**, **Left Status**, **Right Status**, **L+R Status**, **RDS Group A Status**, and **RDS Group B Status**.

### Channel Monitoring

This page displays tables with the following parameters: **Frequency**, **RF** (*level*, *average*, *and peak maximum*), **Multipath** (*level*, *average*, *and peak maximum*), **MPX** (*level*, *average*, *and peak maximum*), **MPX Power** (*level*, *average*, *and peak maximum*), **Pilot** (*level*, *average*, *and peak maximum*), **RDS** (*level*, *average*, *and peak maximum*), **Left/Right** (*level*, *average*, *and peak maximum*), **L+R** (*level*, *average*, *and peak maximum*), **L-R, Temperature** (*level*, *average*, *and peak maximum*), **Fan** (*level*, *average*, *and peak maximum*), **RDS Group**, **RDS Lock**, **RDS PI**, **RDS PS**, **RDS RT**, **RDS TA**, **RDS TP**, **RDS Program**, **RDS PTY**, **RDS BER**, and **Audio Stereo**.

### Channel RDS AF Monitoring

This page displays two tables that monitor RDS AF frequency.

### Tuner Settings

The page provides control over tuner and audio processing and the two RF antenna input settings.

### Alarms Settings

This page contains page buttons to subpages with settings related to alarms, i.e. **Left/Right Audio Settings**, **MPX Settings**, **RF Settings**, **Fand and Temp Settings**, **RDS Settings**, and **Pilot Settings**.

Each page displays several **alarm triggers** for the following parameters: **Left/Right Audio**, **RF**, **MPX**, **MPX Power**, **RDS Group**, **Pilot**, **RDS Levels**, **Temperature**, and **Fan**. In case a parameter exceeds the limits, the device will initiate the sending of an alarm notification via the selected communication path, which can be via **email**, **SMS**, **SNMP trap**, or **GPO**.

### Channel Settings

This page shows the **alarm triggers** for each channel in the **channel tables**.

### Communication Settings

This page contains page buttons with configuration options: **HTTP**, **Application**, **SNMP Agent**, **Network**, **Syslog**, **Streamer**, **Email**, **FTP**, **GSM Modem**, **UECP UDP Server**, and **UECP TCP Server**.

For each of the page buttons, there is also a parameter that can be used to enable or disable them.

### Output Settings

This page displays **GPO settings**. Each GPO has function, type, and pulse time parameters, which can be set individually for each of the GPOs.

### Security Panel

This page displays a block of access/administration parameters.
