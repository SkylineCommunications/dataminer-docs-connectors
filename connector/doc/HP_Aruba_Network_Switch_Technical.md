---
uid: Connector_help_HP_Aruba_Network_Switch_Technical
---

# HP Aruba Network Switch

## About

The HP Aruba Network Switch is designed for monitoring and device configuration. This connector listens for traps from the device, and reads the status and errors of the device.

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

### Status

### Interface

### SNMP

### VLAN

### Events
