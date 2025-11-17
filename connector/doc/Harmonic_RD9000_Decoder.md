---
uid: Connector_help_Harmonic_RD9000_Decoder
---

# Harmonic RD9000 Decoder

The Harmonic RD9000 is a multiformat professional **single or multi-slice UHD decoder that is HDR ready**.

This SNMP connector contains different tables that allow the user to monitor and configure both the input and output.

## About

### Version Info

| Range              | Key Features                                                                                                                 | Based on | System Impact                                          |
|--------------------|------------------------------------------------------------------------------------------------------------------------------|----------|--------------------------------------------------------|
| 1.0.0.x            | - Monitoring. <br>- Configuration of both inputs and outputs.                                                                | -        | -                                                      |
| 1.0.1.x  | - Renamed "Primary SRC" to "Primary Source" (same change applied to "Backup SRC"). <br>- Updated "Ts Bitrate" from bps to Mbps. <br>- Modified "Ts Sync" from "Lock Locked" to "Locked" and from "Lock Unlock" to "Unlock". <br>- Made "Primary Source" a dropdown box, dependent on the "Label" column in the "Input Source" table. <br>- Updated display keys in the "Input Source" and "MPEG IP Receive" tables. <br>- DCF interfaces added.               | 1.0.0.4  | Display key updates and parameter name/value changes. |
| 1.0.2.x [SLC Main] | -Added more decoder related parameters. <br>-Extend display keys for some tables. <br>-Shifted existing discreet values to exception values. <br>-Renamed existing discreet display tags. <br>-Added low range to existing parameters. <br>Updated location of existing tables.               | 1.0.1.1  | -Display key updates for some tables. <br>-Check if there are existing dataminer features (Filters, Automation scripts, Visio files, Reports, Dashboards, Web API) referencing those tables with new display keys. <br>-For parameters with new low range, their alarm templates might need to be reconfigured because they will throw errors and fail to be applied if they have an alarm value configured outside the range.|

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |
| 1.0.1.x   | -                      |
| 1.0.2.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | Yes                 | Yes                     | -                     | -                       |
| 1.0.2.x   | Yes                 | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device (default: *ByPassProxy*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the device.

## How to use

The element created with this connector consists of the following data pages:

### General

- This page contains basic device information, **Network Adapters** and **CPU Cores**.

- It also contains sensors (**Temperature**, **Fans**, **Power Supply**) indicating if the decoder is operational.

### Input
- This page contains inputs related to the decoder.
- Device configuration could be done through some of the provided tables.

### Output
- This page contains outputs related to the decoder.
- Device configuration could be done through some of the provided tables.

### ASI/SDI
- This page contains ASI/SDI info related to the decoder.
- Device configuration could be done through some of the provided tables.

### Decode
- This page contains decoding related info.
- Device configuration could be done through some of the provided tables.
- You can set the desired display key format for the **Decoder** table.

### Service
- This page contains decoded services.
- Device configuration could be done through some of the provided tables.

### Subtitle Overlays
- This page contains subtitle overlays related to the decoded services.
- Device configuration could be done through some of the provided tables.

### Encryption
- This page contains encryption/scrambling related to the decoded services.
- Device configuration could be done through some of the provided tables.

### Alarms
- This page contains alarms reported on the decoder.
- You can set the desired display key format for the **Alarms** table.

### Events
- This page contains events reported on the decoder.

### System Conditions
- This page contains system related info.
- Device configuration could be done through some of the provided tables.

### Polling
- You can set polling configurations of the decoder's data.
