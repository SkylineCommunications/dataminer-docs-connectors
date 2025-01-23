---
uid: Connector_help_IRT_IRPC_Series
---

# IRT IRPC Series

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
- On the **Digital Sensor** page, you'll find the **Digital Sensor** table, with each row represents an individual Digital Sensor.
- **Switch Sensor** page contains the table where each row represents a Switch Sensor.
- The parameters for the **Internal Sensor** can be found on the page with the same name.
- **External Relays** page features two tables that represent the External Relays.
- The Polling configuration can be modified on the *Configuration** page.
