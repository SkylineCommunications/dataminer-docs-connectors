---
uid: Connector_help_FOR-A_FRC-8000
---

# FOR-A FRC-8000

## About

The FOR-A FRC-8000 connector provides monitoring for a FOR-A FRC-8000 frame rate converter over SNMP.

## Key Features

- **General status**: Displays system information, power supply status and temperature, installed options, and SNMP information.
- **Audio status**: Displays the status of SDI and ASI inputs and outputs, and decoder and encoder status.
- **Video status**: Displays the video standard, clock frequency, reference standard, genlock detection, and video I/O synchronization.
- **Web interface**: Provides access to the device web interface from the connector.

## Use Case

Use this connector to monitor the general, audio, and video status of a FOR-A FRC-8000 frame rate converter in DataMiner.

## Technical Reference

The existing documentation records support for device firmware version 1.42.

<<<<<<< Updated upstream
#### SNMPv1 connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device, e.g., *10.11.12.13.*

SNMP Settings:

- **Port number**: The port of the connected device, by default *161.*

## Usage (1.0.0.x)

### General

This page displays general information about the device:

- **General Info**: System information.
- **Power Supply**: Status, temperature.
- **Options**: Installed options.
- **SNMP Info**: Packets information, etc.

### Audio

This page displays the audio statuses of all the SDI and ASI inputs and outputs, as well as the decoder and encoder statuses.

### Video

This page displays the Video Standard, Clock Frequency, Reference Standard, Genlock Detect and Video I/O Sync.

### Web Interface

This page displays the web interface of the device. Note that the client machine has to be able to access to the device, as otherwise it will not be possible to open the web interface.
=======
> [!NOTE]
> For configuration details and page descriptions, refer to the [technical documentation](xref:Connector_help_FOR-A_FRC-8000_Technical).
>>>>>>> Stashed changes
