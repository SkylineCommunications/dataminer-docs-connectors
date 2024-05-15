---
uid: Connector_help_Ciena_CN4200_F10-T
---

# Ciena CN4200 F10-T

This is a Transponder Module for the Ciena CN4200 Chassis.

## About

There are two connector ranges for this connector. The 1.0.0.x range has a fixed number of ports and channels (2), and the port and channel settings are represented as individual parameters.
In the 2.0.0.x range, the ports and channels are shown as tables, which allows for all ports and channels to be shown.

## Configuration

### Connections

#### SNMP connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- IP address/host: The polling IP of the device
- Device Address: The bus address for this particular module.

SNMP Settings:

- Port number: The port of the connected device (default: *161*).
- Get community string: The community string used when reading values from the device (default: *public*).
  Set community string: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## Usage

### General

This page  includes general information about the device, such as **CLEI Code, Primary State, HW Revision**, etc.

### Ports

This page shows information about the ports either in individual parameters (only port 1 and port 2, protocol version 1.0.0.x) or in table format (all ports on the device, protocol version 2.0.0.x).

The displayed information includes the **Port Primary State**, **Port Direction**, **Port Wavelength**, etc.

### Channels

This page shows information about the Channels either in individual parameters (only channel 1 and channel 2, protocol version 1.0.0.x) or in table format (all channels on the device, protocol version 2.0.0.x).

The displayed information includes the **Channel Type*, *Channel Primary State**, etc.

### Web Interface

This page shows the native web interface of the device. This page is only available if the client has access to the device.
