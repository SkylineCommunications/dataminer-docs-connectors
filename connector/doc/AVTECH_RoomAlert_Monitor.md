---
uid: Connector_help_AVTECH_RoomAlert_Monitor
---

# AVTECH RoomAlert Monitor

This connector is used to monitor and configure an AVTECH RoomAlert Monitor device.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*
- **Get community string**: The community string used when reading values from the device. By default *public*.
- **Set community string**: The community string used when setting values on the device. By default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

These are the main data pages of the connector:

- The **General** page provides general information about the device, including its **Name** and **Contact** details.
- The **Digital Sensor** and **Switch Sensor** pages each contain a table where each row represents an individual digital sensor or switch sensor, respectively.
- The **Internal Sensor** page contains the parameters for the internal sensor.
- The **External Relays** page features two tables that represent the external relays.
- On the **Configuration** page, you can modify the polling configuration.
