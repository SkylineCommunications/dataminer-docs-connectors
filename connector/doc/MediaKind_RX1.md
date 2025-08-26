---
uid: Connector_help_MediaKind_RX1
---

# MediaKind RX1

The MK RX1 is a multi-codec multi-service professional decoder.

The MediaKind RX1 connector focuses on monitoring the configuration found in the device. It gives an overview of the inputs, decryption settings, demodulation settings, and outputs.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | Initial version (monitoring of configuration parameters). | - | - |
| 1.0.1.x | Configurable display key on Active Alarms. | 1.0.0.3 | May affect visual overviews, Automation scripts, trending, alarms, etc. |
| 1.0.1.x | - Decryption Table display key updated.<br>- SDI Outputs table columns are now writable.<br>- Video and Audio status columns.<br>- Decoding service selection. | 1.0.1.8 | May affect visual overviews, Automation scripts, alarms, etc. |
| 1.1.0.x [SLC Main] | - Changed JSON properties have been updated.<br>- Program number, IP sources, and source addresses are now editable.<br>- DCF interfaces added.<br>- Redundancy Mode parameter discreets updated. | 1.0.2.5 | Not backwards compatible with older versions. SDI Outputs table will not be filled in because of the mismatch. |
| 1.3.0.x | - JSON properties for SRT input commands are changed | 1.1.0.27 | Not backwards compatible with older versions. SRT Inputs and outputs table sets won't work because of adjusted JSON. |

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

No extra configuration is needed. The device does not require authentication.

### Redundancy

There is no redundancy defined.

## How to use

The connector is only used for monitoring, so no special settings are required.

## Notes

This connector has been developed using the information available in version 6.0 of the API. The connector monitors the configuration of the device and the status of the signals.
