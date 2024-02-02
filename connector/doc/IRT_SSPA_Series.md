---
uid: Connector_help_IRT_SSPA_Series
---

# IRT SSPA Series

This connector is used to monitor and configure an IRT SSPA Series device.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.12.10                |

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

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device. By default *public*.
- **Set community string**: The community string used when setting values on the device. By default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

These are the main data pages of the connector:

- The **Monitor** page is the default page. Here you can find information about **Input** and **Output** power, **Device Temperature**, and **Mute status**.
- The **General** page displays general information about the connector, such as the **Name** and **Location** of the device.
- The **Alarms** page contains the **System Alarms Table**, which shows information about alarms such as the **Description**, **Status**, and **Device Name**.
- On the **Control** page, you can change **Mute** and **Gain** values.
- On the **Configuration** page, you can configure the **Center Frequency** and **Attenuation Offset**. On the **LO Settings** subpage, you can find the **LO Frequencies** table.
- The **Redundancy** page contains information about the redundancy members.

When the connector is working properly, every table on every page should be populated accordingly. If necessary, you can double-check this by looking at the parameters on the web interface.

If everything works correctly, in the Stream Viewer you will be able to see groups **100**, **110**, **1000**, **2000**, **2010**, **2020**, and **8000**.

- Groups **2020** and **8000** represent parameters that are checked every 10 seconds.
- Groups **100**, **110**, **1000**, **2000**, and **2010** are checked every 5 minutes.
- If there is a polling error with any of the groups, the Stream Viewer will return **GENERIC ERROR** in the response from the device.
