---
uid: Connector_help_Imagine_Communications_Platinum_VX_4RU_Technical
---

# Imagine Communications Platinum VX 4RU

## About

Platinum VX 4RU is a small-to-midsize utility video router capable of handling 144×144 modular I/O with optional SFP connectivity.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element consists of the following data pages:

- **General**: Contains general device information and settings.
	- **Power Supply**: Manage the power supplies available.
	- **Switch Point**: Configure the switch points and their delays.
	- **Fans**: Check the state of the fans and their speeds.
	- **Resource Cards**: Contains information of the two available resources.
	- **Clock**: Clock information coming from the device.
- **Module Statuses**: Contains a table with the states for each module. 
- **Network Configurations**: Configure several network parameters of the device.
- **Alarm Configurations**: Has a table with configurations for several alarm configurations.
- **Matrix View**: Contains the video I/O routings.
	- **Routing**: Contains the tables that fill in the matrix.
- **Faults**: Contains all the faults reported by the device.