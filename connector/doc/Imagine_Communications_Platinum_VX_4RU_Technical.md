---
uid: Connector_help_Imagine_Communications_Platinum_VX_4RU_Technical
---

# Imagine Communications Platinum VX 4RU

## About

Platinum VX 4RU is a small-to-midsize utility video router capable of handling 144x144 modular I/O with optional SFP connectivity.

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

  - **Power Supply**: Allows you to manage the available power supplies.
  - **Switch Point**: Allows you to configure the switch points and their delays.
  - **Fans**: Displays the state of the fans and their speeds.
  - **Resource Cards**: Contains information about the two available resources.
  - **Clock**: Contains clock information from the device.

- **Module Statuses**: Contains a table with the states for each module.

- **Network Configurations**: Allows you to configure several network parameters of the device.

- **Alarm Configurations**: Contains a table with alarm configuration settings.

- **Matrix View**: Contains the video I/O routings.

  - **Routing**: Contains the tables that the matrix is based on.

- **Faults**: Displays the faults reported by the device.
