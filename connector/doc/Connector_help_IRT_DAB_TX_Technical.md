---
uid: Connector_help_IRT_DAB_TX_Technical
---

# IRT DAB TX

## About

The IRT DAB TX is designed for continuous monitoring of DAB signals. This connector controls the inputs, listens for traps from the device, and reads the status and errors of the device.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General Page

This page displays general information.

### Single Transmitter

This page displays the Single Transmitter information.

### Dual Drive

This page displays Dual Drive Transmitter information.

### Polling Settings

On this page, you can define the polling groups of the element.

### SNMP

On the SNMP page, there is a table that allows the user to enter information to retrieve data from a specific OID. It´s also possible to set an optional trap receiver IP.
