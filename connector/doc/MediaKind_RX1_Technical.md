---
uid: Connector_help_MediaKind_RX1_Technical
---

# MediaKind RX1

The MK RX1 is a multi-codec multi-service professional decoder. This connector can be used to monitor the configuration of this device. It provides an overview of the inputs, decryption settings, demodulation settings, and outputs.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [Deprecated] | Initial version (monitoring of configuration parameters). | - | - |
| 1.0.1.x [Deprecated] | Configurable display key on Active Alarms. | 1.0.0.3 | May affect visual overviews, Automation scripts, trending, alarms, etc. |
| 1.0.2.x [Deprecated] | - Decryption Table display key updated.<br>- SDI Outputs table columns are now writable.<br>- Video and Audio status columns.<br>- Decoding service selection. | 1.0.1.8 | May affect visual overviews, Automation scripts, alarms, etc. |
| 1.1.0.x [Active] | - Changed JSON properties have been updated.<br>- Program number, IP sources, and source addresses are now editable.<br>- DCF interfaces added.<br>- Redundancy Mode parameter discreets updated. | 1.0.2.5 | Not backwards compatible with older versions. SDI Outputs table will not be filled in because of the mismatch. |
| 1.2.0.x [Active] | Added authentication for API calls. | 1.1.0.26 | Not backwards compatible with older versions. |
| 1.3.0.x [Active] | JSON properties for SRT input commands have been changed. | 1.1.0.27 | Not backwards compatible with older versions. SRT Inputs and Outputs table sets will not work because of adjusted JSON. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 11.0.4.0               |
| 1.0.1.x   | 11.0.4.0               |
| 1.0.2.x   | 11.0.4.0               |
| 1.1.0.x   | 16.2.1.1               |
| 1.2.0.x   | 15.X                   |
| 1.3.0.x   | 16.5.1.2               |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | Yes                 | Yes                     | -                     | -                       |
| 1.2.0.x   | Yes                 | Yes                     | -                     | -                       |
| 1.3.0.x   | Yes                 | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).

## How to use

Once an element has been created, polling will start, and information will be shown on the following pages:

- **Servers:** Contains information about the servers on the device as well as their statistics. Via the Servers table, you can reboot each server.
- **Services:** Contains information about the services available on the device as well as their statistics and programs. Services can be started or stopped through the Services table.
- **Input:** Contains all input information for each available source and stream. All configurations regarding inputs can be configured through the tables on this page.
- **Processing:** Contains an overview of all processing streams on the device.
- **Decryption:** Contains information about all service decryptions. The configuration for each service decryption can be adjusted through the Decryption table.
- **Decoding:** Contains information about all available decoding resources. The configuration can be adjusted through the Decoding table.
- **Outputs:** Contains information about output services. Output service can be enabled or disabled through the Outputs table.
- **Reliable Transport:** Contains information about SRT services. Via the tables on this page, you can adjust the input or output mode for each service as well as configure the SRT Listener, SRT Caller, or UDP configuration for each service.
- **Alarms:** Contains information about the alarms related to the MediaKind RX1 device.
- **Traps:** Contains information about detected traps in the MediaKind RX1 device.

## Notes

This connector has been developed using the information available in version 6.0 of the API. The connector monitors the configuration of the device and the status of the signals.
