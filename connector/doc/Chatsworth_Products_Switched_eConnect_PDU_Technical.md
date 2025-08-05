---
uid: Connector_help_Chatsworth_Products_Switched_eConnect_PDU_Technical
---

# Chatsworth Products Switched eConnect PDU

## About

Switched eConnect PDUs provide remote monitoring of power at the rack level and individual outlet control, making it possible to remotely turn power on or off at each outlet. It is designed for advanced data center power management and can be controlled remotely via web or SNMP to turn individual outlets on/off or reboot devices.

## Configuration

### Connections

#### SNMP Connection - Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.

SNMP Settings:

- **Port number**: The port of the connected device, by default 161.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector functions as a monitoring tool of the Switched eConnect PDU. It monitors information such as the PDU Branch, Outlets, and Sensors.
