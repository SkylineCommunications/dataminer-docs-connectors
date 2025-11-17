---
uid: Connector_help_Harmonic_ViBE_CP9000
---

# Harmonic ViBE CP9000

The Harmonic ViBe CP9000 is a contribution encoder that preserves video quality at the front of the broadcast chain by processing uncompressed UHD signals.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | - Monitoring. <br>- Configuration of the device. | - | - |
| 1.0.1.x | - Monitoring. <br>- Configuration of the device. | 1.0.0.2 | The display key of the Alarms table and Sub System Info table has changed. |
| 1.0.2.x [SLC Main] | - HTTP Connection. | 1.0.1.6 | - Element reconfiguration: Existing elements need to be reconfigured before the new connection(s) will be taken in use. <br>- Ensure that your encoder's firmware is 2.1-ed-A and above. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.0-ed-A               |
| 1.0.1.x   | 2.0-ed-A               |
| 1.0.2.x   | 2.1-ed-A               |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### HTTP Secondary connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the Ciena Blue Planet Operate.
- **IP port**: The port to communicate with the API.
- **Bus address**: By default *bypassproxy.*

### Web Interface

- The web interface is only accessible when the client machine has network access to the device.

## How to use

### General

- This page contains product information, such as the **System Name**, **System Description**, and **Serial Number**. It also displays the primary and secondary alarm output status.

### Authorization

- You will need to provide the credentials required for HTTP communication.

### HW/SW Info

- On this page, you can monitor the **Board Info**, **Software Licenses**, and **Inventory Info** tables.

### Alarms

This page contains the following tables:

- **Sub System** **Info**: Lists alarms related to one chassis function and one function-encoding channel.
- **Alarms**: Lists the alarms that are present on the device.

### Events

- This page contains a table with information regarding events for which the operator should be notified, such as alarm that have been raised or dropped.

### IP

- On this page, the **IP Interfaces** table lists all external IP interfaces.

### Maintenance

- On this page, you can find configurable parameters such as **BCAST Status** and **Transfer Buffer Max Size**. Two buttons are available, **Reboot** and **Shutdown**, which allow you to execute the corresponding actions on the device.

### Presets

- This page contains a read-only table listing the previously saved configurations.

### Traps

- On this page, the **Manager Table** displays the configured trap destinations.

### Encoder Services
- This page contains the encoded services and its' components.
- Device configuration can be done through some of the provided tables.

### Encoder Video
- This page contains the video components of the encoded services.
- Device configuration can be done through the provided tables.

### Encoder Input Audio
- This page contains the input configurations for the audio components of the encoded services.

### Encoder Output Audio
- This page contains the output configurations for the audio components of the encoded services.
- Device configuration can be done through the provided table.

### Encoder SCTE-35
- This page contains the SCTE-35 components of the encoded services.
- Device configuration can be done through the provided table.

### SMPTE2022-6 Subscriptions
- This page contains the SMPTE2022-6 subscriptions of the encoded services.
- Device configuration can be done through the provided table.

### Transport Stream Outputs
- This page contains the transport stream outputs of thge encoded services.
- Device configuration can be done through the provided tables.

### Polling
- You can set polling configurations of the decoder's SNMP data.

### Alarm Custom Definition
- You can set custom names for alarms based of their identifier and name.
