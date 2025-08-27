---
uid: Connector_help_MediaKind_RX1_Technical
---

# MediaKind RX1

The MK RX1 is a multi-codec multi-service professional decoder. This connector can be used to monitor the configuration of this device. It provides an overview of the inputs, decryption settings, demodulation settings, and outputs.

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
