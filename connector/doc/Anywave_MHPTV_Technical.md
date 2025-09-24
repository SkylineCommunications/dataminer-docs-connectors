---
uid: Connector_help_Anywave_MHPTV_Technical
---

# Anywave MHPTV

## About

The Anywave MHPTV connector enables monitoring and control of Anywave MHPTVs. This connector is capable of retrieving and setting data using SNMP to communicate with the Transmitter.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]

SNMP Settings:

- **IP port**: [The IP port of the destination.]
- **Get community string**: [The community string used when reading values from the device. (default: *public*)]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### Transmitter Page

The Transmitter Page gives a comprehensive overview of the Transmitter's operational status and key parameters such as `Forward Power` and `Reflective Power` as well as the alarm status of these parameters.

### System Configuration

The System Configuration page allows for the management of the Transmitter as well as the Exciter.
