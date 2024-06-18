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
| 1.0.1.x [SLC Main] | - Decryption Table display key updated.<br>- SDI Outputs table columns are now writable.<br>- Video and Audio status columns.<br>- Decoding service selection. | 1.0.1.8 | May affect visual overviews, Automation scripts, alarms, etc. |
| 1.1.0.x | - Updated the JSON properties that have been changed.<br>- Program number, IP sources, Source Addresses are now writable.<br>- Added DCF interfaces<br>- Updated the discreets in the Redundancy Mode parameter. | 1.0.2.5 | Not backwards compatible with older versions. SDI Outputs table will not be filled because of the mismatch. |
### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 11.0.4.0               |
| 1.0.1.x   | 11.0.4.0               |
| 1.0.2.x   | 11.0.4.0               |
| 1.1.0.x   | 16.2.1.1               |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | Yes                 | Yes                     | -                     | -                       |

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

Currently, the API provided by the vendor is still in its infancy. This connector has been developed using the information available in version 3.0 of the API. However, this means that only the configuration on the device can be monitored, not the status of the signals and processes.
