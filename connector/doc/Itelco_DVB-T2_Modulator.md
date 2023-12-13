---
uid: Connector_help_Itelco_DVB-T2_Modulator
---

# Itelco DVB-T2 Modulator

This connector allows you to monitor and manage the Itelco DVB-T2 Modulator with **SNMP**.

## About

### Version Info

| Range   | Key Features     | Based on | System Impact |
|---------|------------------|----------|---------------|
| 1.0.0.x | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware           |
|---------|------------------------------|
| 1.0.0.x | P3_1_02_358 build 1615742091 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

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

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## Usage

### General Page

This page displays general information and system information on the Itelco device.

### Tx

This page displays parameters related to the transmitter power and the exciter. You can also control exciter-related parameters here.

### Tx Status

This page displays status information for the transmitter in the **Exciter Status** and **RF Alarm** table

### DVB-T

This page displays information related to DVB-T2, with the **Pre-corrector Nonlinear Monitor MER2** parameter.

### Alarm Configuration

This page contains the Alarm Configuration Table. In this table, you can check and change settings for alarm categories.
