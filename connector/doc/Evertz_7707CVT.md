---
uid: Connector_help_Evertz_7707CVT
---
# Evertz 7707CVT

The Evertz 7707CVT-X is an analog video fiber transmitter for broadcast-quality video signals. X stands for the number of inputs.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **Device address**: Indicate if required or not. If it is, specify default value and range.

SNMP Settings:

- **Port number**: The port of the connected device, by default 161.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to use

The element created with this connector will have 5 data pages. The **General** page contains the most important status parameters. Next to this, there is an **Audio** and **Video** page. On the **Faults** page, you can make the device send traps in certain situations. The **Configuration** page contains information about the slot and master jumper.
