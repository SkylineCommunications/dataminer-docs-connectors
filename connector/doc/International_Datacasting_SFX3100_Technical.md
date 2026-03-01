---
uid: Connector_help_International_Datacasting_SFX3100_Technical
---

# International Datacasting SFX3100

## About

The International Datacasting SFX3100 is designed for continuous monitoring. This connector listens for traps from the device, and reads the status and errors of the device.

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

This element created with this connector has the following data pages:

- **General/Measurements**: These pages display general information.
- **Input/Output**: These pages display the device information.
- **Alarms/Notifications**: These pages display alarm and notifications status.
- **Polling Settings**: This page allows you to define the polling groups of the element.
