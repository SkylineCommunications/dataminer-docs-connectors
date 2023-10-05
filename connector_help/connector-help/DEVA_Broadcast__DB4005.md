---
uid: Connector_help_DEVA_Broadcast__DB4005
---

# DEVA Broadcast DB4005

The **DB4005** is a third-generation digital FM Radio Modulation Analyzer.

## About

The device is able to check FM channels. It contains a round-robin system that does not keep track of the status parameters. The time each channel should be measured by the round-robin engine is actively checked and adjusted on the device in order to know which channel is being monitored. Once the channel is known, the status parameters are polled and a table is built with status data for the channels.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \[SLC Main\] | Initial version. | \-           | \-                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | \-                     |

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

### Front Panel

This page contains two page buttons:

- The **Product Info** page button displays the firmware revision and the serial number of the device.
- The **Security Panel** page button displays a block of access/administration parameters.

The page also contains a number of parameters, among others the **Tuner Settings**, which provide control over tuner and audio processing and the two RF antenna input settings.

### Output Settings

This page displays two blocks of parameters: **GPO settings** and **Audio/MPX Output.** The general purpose output settings are applied through this page. In the Audio/MPX output section you can configure the Audio and MPX outputs. Function, type and pulse time for each of the GPOs can be set individually.

### Communication Settings

This page contains 12 page buttons with configuration options, namely **GSM Modem**, **UECP UDP**, **UECP TCP**, **Syslog**, **Streamer**, **Email**, **SNTP**, **FTP**, **HTTP**, **Application**, **SNMP** and **Ethernet**. It also displays a block with a parameter corresponding to each of the page buttons, with the enable/disable option for each of them.

### Alarms Settings

This page displays several **Alarms Triggers** for the following parameters: **RF**, **MPX**, **MPX Power**, **Left/Right Audio**, **RDS Group**, **Pilot**, **RDS Levels**, **Temperature** and **Fan**. In case a parameter exceeds the limits, the device will initiate the sending of an alarm notification via the selected communication path, which can be via **Email**, **SMS**, **SNMP Trap** or **GPO**.

### Status Page

This page shows the **alarm status** of each parameter of the preset frequencies. A **Channel Status Table** is displayed, in which each entry matches with a channel that is being monitored.

### Logger Interface

On this page, you can select and monitor up to 50 radio frequencies by applying the necessary settings. When adjustments are made, the device will monitor all of the selected frequencies at regular intervals. Every channel consists of group settings, which are used when monitoring and alerting. Measurement windows can be set for each of the alarms, including trigger and alarm release times.

### Monitoring

This page displays a table that contains the current channel that is being monitored. The following parameters are evaluated: **Frequency**, **RF** (level, average and peak maximum), **Multipath** (level, average and peak maximum), **MPX** (level, average and peak maximum), **MPX Power** (level, average and peak maximum), **Pilot** (level, average and peak maximum), **RDS** (level, average and peak maximum), **Left/Right** (level, average and peak maximum), **LPR** (level, average and peak maximum), **LMR, Temperature** (level, average and peak maximum), **Fan** (level, average and peak maximum), **RDS Group**, **RDS Lock**, **RDS PI**, **RDS PS**, **RDS RT**, **RDS TA**, **RDS Music speech**, **RDS TP**, **RDS PTY**, **RDS BER** and **Audio Stereo**.

