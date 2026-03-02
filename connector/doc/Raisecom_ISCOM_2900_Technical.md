---
uid: Connector_help_Raisecom_ISCOM_2900_Technical
---

# Raisecom ISCOM 2900

## About

The **Raisecom ISCOM 2900** connector integrates Raisecom devices into monitoring platforms via the SNMP protocol. It supports both **ISCOM 29XX** and **RAX 7XX** series, providing visibility into system metrics, hardware health, and optical transceiver data.

The connector supports SNMP trap communication, delivering real‑time event notifications, primarily related to device shutdowns and other critical events.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.

SNMP Settings:

- **Port number**: The port of the connected device, by default 161.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

#### SNMP Connection - Traps

For trap handling, the connector requires similar input parameters:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.

SNMP Settings:

- **Port number**: The port of the connected device, by default 162.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

To start retrieving data with the Raisecom SNMP Connector, you first have to validate the Device Type parameter. By default, the connector is configured for the *ISCOM 29XX* series; however, this setting can be modified to support devices from the *RAX 27XX* series when required.

Once configured, the connector automatically populates the relevant parameters and tables, providing a consolidated view of device performance and health metrics.
