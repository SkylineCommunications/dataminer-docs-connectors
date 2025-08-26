---
uid: Connector_help_MediaKind_RX1_Technical
---

# MediaKind RX1

The MK RX1 is a multi-codec multi-service professional decoder.

The MediaKind RX1 connector focuses on monitoring the configuration found in the device. It gives an overview of the inputs, decryption settings, demodulation settings, and outputs.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [Deprecated] | Initial version (monitoring of configuration parameters). | - | - |
| 1.0.1.x [Deprecated] | Configurable display key on Active Alarms. | 1.0.0.3 | May affect visual overviews, Automation scripts, trending, alarms, etc. |
| 1.0.1.x [Deprecated] | - Decryption Table display key updated.<br>- SDI Outputs table columns are now writable.<br>- Video and Audio status columns.<br>- Decoding service selection. | 1.0.1.8 | May affect visual overviews, Automation scripts, alarms, etc. |
| 1.1.0.x [SLC Main] | - Changed JSON properties have been updated.<br>- Program number, IP sources, and source addresses are now editable.<br>- DCF interfaces added.<br>- Redundancy Mode parameter discreets updated. | 1.0.2.5 | Not backwards compatible with older versions. SDI Outputs table will not be filled in because of the mismatch. |
| 1.3.0.x [SLC Main] | - JSON properties for SRT input commands are changed | 1.1.0.27 | Not backwards compatible with older versions. SRT Inputs and outputs table sets won't work because of adjusted JSON. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 11.0.4.0               |
| 1.0.1.x   | 11.0.4.0               |
| 1.0.2.x   | 11.0.4.0               |
| 1.1.0.x   | 16.2.1.1               |
| 1.3.0.x   | 16.5.1.2               |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | Yes                 | Yes                     | -                     | -                       |
| 1.3.0.x   | Yes                 | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).

### Initialization

No extra configuration is needed. The device does not require authentication. Once element is created with correct device IP and port, polling cycle will start and all informations about device services will be presented in tables.

## How to use

Once initialized, polling cycle is started and all informations are being showned and monitored.

Device consists of following pages:
- **Servers:** Contains all informations about servers on device as well as their statistics. Reboot can be performed of each server through Servers table.
- **Services:** Contains informations about all services available on device as well as their statistics and programs. Services can be started/stopped through Services table.
- **Input:** Contains info about all input informations for each available source and stream. All configurations regarding inputs can be configured through tables that are presented on this page.
- **Processing:** Contains overview of all processing streams on device.
- **Decryption:** Contains informations about all service decryptions. All configuration for each service decryption can be configured through Decryption table.
- **Decoding:** Contains informations about all available decoding resources. All configurations can be adjusted through Decoding table
- **Outputs:** Contains information about output services. Output service can be enabled/disabled through Outputs table.
- **Reliable Transport:** Contains all informations about SRT services. Through present tables we can adjust input or output mode for each service as well as configure all SRT Listener, SRT Caller or UDP configurations for each service.
- **Alarms:** Contains informations about all alarms regarding MediaKind RX1 device.
- **Traps:** Contains all informations about detected traps in MediaKind RX1 device.

## Notes

This connector has been developed using the information available in version 6.0 of the API. The connector monitors the configuration of the device and the status of the signals.
