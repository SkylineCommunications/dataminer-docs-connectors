---
uid: Connector_help_Qbit_Q565
---

# Qbit Q565

The Qbit Q565 is a FM DVB transcoder providing up to 8 FM radio channels.

## About

This connector is used to control and monitor the Qbit Q565.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | v2.220                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device. (default: public)
- **Set community string**: The community string used when setting values on the device. (default: private)

## Usage

### General

Contains general information about the device.

### Encoder

Contains information related to the encoder channels.

### FM

Contains information related to the frequency modulator.

### PSI

Contains information regarding the Program Specific Information a metadata pertaining to MPEG transport stream.

### Output

Contains information and editable settings regarding the output.

### Alarms

Contains alarming information.

### SD Card

Contains the status of the SD card.

### Backup/Restore

Contains settings to backup and restore things from the device.

### Web Interface

Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
