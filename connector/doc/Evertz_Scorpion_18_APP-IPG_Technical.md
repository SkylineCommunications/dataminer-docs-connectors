---
uid: Connector_help_Evertz_Scorpion_18_APP-IPG_Technical
---

# Evertz Scorpion 18 APP-IPG

## About

The SCORPION-18 APP-IPG is a software app that turns a SCORPION-18 frame into a high-density IP media gateway, encapsulating/de-encapsulating SDI (up to 12G) to/from SMPTE ST 2110 (and, in variants, ST 2022-6), with hitless 2022-7 support. It runs on the SCORPION-18's NETAD compute and provides multiple configurable gateway paths.

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

This connector functions as a monitoring tool for the Scorpion 18 APP-IPG. It monitors important information like SDI Input, SDI Output, and various Notify tables.
