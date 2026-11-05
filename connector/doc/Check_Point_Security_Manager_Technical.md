---
uid: Connector_help_Check_Point_Security_Manager_Technical
---

# Check Point Security Manager

## About

The Check Point Security Manager is a comprehensive software solution for managing security policies and firewalls.

## Configuration

### Connections

#### SNMP Main Connection

This connector uses an SNMPv2 connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use (1.0.0.x)

The element created with this connector consists of the following data pages:

- **General**: Displays general **system information** as well as the **System OR** table, which lists the capabilities of the local SNMP applications acting as a command responder with respect to various MIB modules.
- **Management**: Displays the **Connected Clients** table, **Connected Gateways** table, and **Indexer Info**.
- **Web Interface**: Displays the web interface of the polling IP address.
