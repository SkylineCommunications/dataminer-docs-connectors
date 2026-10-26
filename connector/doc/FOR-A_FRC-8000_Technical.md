---
uid: Connector_help_FOR-A_FRC-8000_Technical
---

# FOR-A FRC-8000

## About

The FOR-A FRC-8000 connector monitors a FOR-A FRC-8000 frame rate converter over SNMP. It provides general device, audio, and video status, as well as access to the device web interface.

## Configuration

### Connections

#### SNMP Main Connection

This connector uses an SNMPv1 connection and requires the following input during element creation:

- **IP address/host**: The polling IP address of the device.
- **IP port**: The SNMP port of the device (default: *161*).
- **Bus address**: Not required.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

The **General** page displays system information, power supply status and temperature, installed options, and SNMP information.

### Audio

The **Audio** page displays the status of the SDI and ASI inputs and outputs, as well as decoder and encoder status.

### Video

The **Video** page displays the video standard, clock frequency, reference standard, genlock detection, and video I/O synchronization.

### Web Interface

Use the **Web Interface** page to view the device web interface. The client machine must have network access to the device.

## Notes

The existing documentation records support for device firmware version 1.42.
