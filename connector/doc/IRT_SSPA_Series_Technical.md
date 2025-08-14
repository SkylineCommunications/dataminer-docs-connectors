---
uid: Connector_help_IRT_SSPA_Series_Technical
---

# IRT SSPA Series

## About

This connector is used to monitor and configure an IRT SSPA Series device.

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.12.10                |
| 1.0.1.x   | 2.12.10                |

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
