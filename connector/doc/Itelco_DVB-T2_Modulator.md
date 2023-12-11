---
uid: Connector_help_Itelco_DVB-T2_Modulator
---

# Itelco DVB-T2 Modulator

This connector allows you to monitor and manage the Itelco DVB-T2 Modulator with **SNMP**.

## About

### Version Info

| **Range**     | **Description**                                                                            | **DCF Integration** | **Cassandra Compliant** |
|----------------------|--------------------------------------------------------------------------------------------|---------------------|-------------------------|
| 1.0.0.x              | Initial version.                                                                           | No                  | Yes                     |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | P3_1_02_358 build 1615742091 |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP settings:

- **Port number**: The port of the connected device, by default *161.*
- **Get community string**: The community string in order to read from the device. The default value is *public*.
- **Set community string**: The community string in order to set to the device. The default value is *private.*

## Usage

### General Page

This page displays general information and system information on the Itelco device.

### Tx

This page displays Transmitter power and Exciter related parameters also allowing users to control the Exciter related parameters.

### Tx Status

This page displays the transmitter related status, It consists of the Exciter Status and RF Alarm table

### DVB-T

This page displays the DVB-T2 related information. It consists of the Pre-corrector Nonlinear Monitor MER2 parameter.

### Alarm Configuration

This page contains the Alarm Configuration Table. Allowing users to check and change settings for Alarm categories.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

