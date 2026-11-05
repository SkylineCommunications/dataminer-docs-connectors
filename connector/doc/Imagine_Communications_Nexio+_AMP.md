---
uid: Connector_help_Imagine_Communications_Nexio+_AMP
---

# Imagine Communications Nexio+ AMP

## About

The Nexio+ AMP video server combines Hewlett Packard Enterprise standard server models and Imagine software/hardware bundle kits, enabling software-defined applications and allowing broadcast operations to reliably and flexibly manage digital content from ingest to playout.

This connector is meant to work with the Imagine Communications Nexio+ AMP video server. The connector shows basic information of the different communication methods and connections the device is currently using.

### Version Info

| Range              | Description     | DCF Integration | Cassandra Compliant |
|--------------------|-----------------|-----------------|---------------------|
| 1.0.0.x (Obsolete) | Initial version | No              | Yes                 |
| 1.0.1.x (Obsolete) |                 | No              | Yes                 |
| 1.1.0.x (SLC Main) | Firmware change | No              | Yes                 |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

## Usage

### Interface

The Interface Table shows the different interfaces that the device is connected to and their various network traffic statistics, including bandwidth and bit rate.

### IP Status

This pages shows information on the IP protocol communication traffic to and from the device. This includes tables showing the connection addresses, the different routes, and the translations.

### ICMP Status

This pages shows information on the ICMP protocol communication traffic to and from the device.

### TCP Status

This pages shows information on the TCP protocol communication traffic to and from the device. This includes a table showing the different TCP connections.

### UDP Status

This pages shows information on the UDP protocol communication traffic to and from the device. This includes a table showing the UDP listeners.

### SNMP Status

This pages shows information on the SNMP protocol communication traffic to and from the device.

### Server Info

This page shows server information including the name, version, uptime, and memory information. There is also a table showing the loaded device drivers and one showing the loaded file names.

### VR Status

This pages has two tables showing the virtual internal and external disks on the server.

### OS Alarms

This page shows information about memory and CPU thresholds and shows an internal disk table.

### Network

This table shows the network cards that the machine has loaded.

### Hardware

This page has domain, CPU usage, and hardware information.
