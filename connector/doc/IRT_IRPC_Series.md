---
uid: Connector_help_IRT_IRPC_Series
---

# IRT IRPC Series

This connector is used to monitor and configure an IRT IRPC Series device.

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

- The **Redundancy** page serves as the default page. Here you can access the **Units** table and switch between units.
- The **General** page provides general information about the device, including its **Name** and **Contact** details.
- On the **Alarms** page, you can view the **System** and **Unit** tables, which display information such as the alarm **Description** and **Status**.
- Available modules are listed in the **Device Modules** table on the **Device** page.
- The **Controls** page contains the **Configuration** table, where you can adjust settings such as **Attenuation**, **Gain**, and **Mute**.
