---
uid: Connector_help_GatesAir_MSCx_Np1_Technical
---

# GatesAir MSCx Np1

## About

The GatesAir Multi-System Controller (MSCx) manages redundancy in radio and television transmitter systems, offering seamless failover control between main and backup transmitters in N+1 or dual configurations.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: The device address of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).
