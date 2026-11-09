---
uid: Connector_help_FOR-A_FRC-8000_Technical
description: "Configure SNMP connectivity and monitor general device, audio, and video status information for the FOR-A FRC-8000 frame rate converter."
---

# FOR-A FRC-8000

## About

The FOR-A FRC-8000 connector monitors a FOR-A FRC-8000 frame rate converter over SNMP. It provides general device, audio, and video status information, as well as access to the device web interface.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses an SNMPv1 connection and requires the following input during element creation:

- **IP address/host**: The polling IP address of the device.
- **IP port**: The SNMP port of the device (default: *161*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General Page

This page displays system information, the power supply status and temperature, installed options, and SNMP information.

### Audio Page

This page displays the status of the SDI and ASI inputs and outputs, as well as decoder and encoder status.

### Video Page

This page displays the video standard, clock frequency, reference standard, genlock detection, and video I/O synchronization.

### Web Interface Page

Use this page to view the device web interface. The client machine must have network access to the device.

## Notes

- Supports device firmware version 1.42.
