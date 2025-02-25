---
uid: Connector_help_Promax_Neo
---

# Promax Neo

## About

The Promax Neo is a portable device used to analyze and measure the quality of electronic signals.

This connector is used to monitor and configure the device data using SNMP communication.

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

## How to use

This connector uses SNMP to retrieve information from the card. It displays the information on the pages and allows you to perform changes to it.
