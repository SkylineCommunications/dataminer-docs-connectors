---
uid: Connector_help_Snell_Wilcox_IQADA00
---

# Snell Wilcox IQADA00

The IQADA00 is a single/dual-channel analog audio distribution amplifier. It provides dual analog inputs with up to five outputs per input, or a single analog input with up to ten outputs.

## About

This connector provides status data for input 1 and input 2. It is also possible to set certain control parameters.

### Version Info

| Range   | Description                                                                                                                    | DCF Integration | Cassandra Compliant |
|---------|--------------------------------------------------------------------------------------------------------------------------------|-----------------|---------------------|
| 1.0.0.x | This version treats the boards contained within the chassis as DVEs.                                                           | No              | Yes                 |
| 2.0.0.x | This version should be used to monitor each board separately (i.e. each board is represented by a single independent element). | No              | Yes                 |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | Unknown                     |
| 2.0.0.x          | 5.3. .6                     |

## Configuration

### Connections - Range 1.0.0.x

#### SNMP main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: Not required.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used to read from the device. The default value is *public*.
- **Set community string**: The community string used to write on the device. The default value is *private.*

### Connections - Range 2.0.0.x

#### SNMP main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: The ID of the board to be monitored.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used to read from the device. The default value is *public*.
- **Set community string**: The community string used to write on the device. The default value is *private.*

## Usage

### General

This page contains general parameters related to the device: **Serial Number**, **Software Version**, etc.

### Configuration

This page contains **gain** and **silence** parameters. There are also buttons to **preset** and **restart** the unit.

### Log

This page contains status and **control parameters** for input 1 and input 2.

### Roll Track

This page contains **roll track parameters** for index and index B.
