---
uid: Connector_help_ZTE_ZXDU
---

# ZTE ZXDU

## Overview

The ZTE ZXDU is a Centralized System Management Unit (CSU501B) designed for front-end monitoring of the communication DC power supply system. It plays a crucial role in tracking and managing the operational status of the system, ensuring efficient and reliable power management.

The CSU501B features an RJ45 Ethernet interface for network connectivity, a USB interface for data export, indicators for system status, an LCD for display, and buttons for navigation and settings.

It includes multiple functions:

- **Management**: The CSU501B supports comprehensive management features, including charging, discharging, and test management of battery sets. It also controls the automatic sleep of rectifiers to save energy and exports historical records through a USB flash drive.

- **Alarm**: When faults occur, the CSU501B reports alarms and takes protective measures, including over-voltage protection (output), and over-/under-voltage protection (input).

- **Monitoring**: Operational data of the power system is collected, and its status is monitored in real time. The device can report data to the Supervision Center and monitor the power system remotely.

- **Wireless Communication**: The unit supports GPRS and 3G network modes, providing SMS and email notifications for efficient remote communication.

- **Web Functions**: With network connectivity, users can access the CSU501B using Chrome to read data in real time and configure the unit.

- **SNMP**: When connected to a network, SNMP software can be used for real-time data reading and configuration of the CSU501B.

### Version Info

| Range   | Key Features                                                      | Based on | System Impact |
|---------|-------------------------------------------------------------------|----------|---------------|
| 1.0.0.x | - Initial version. <br>- Compatibility with Skyline EPM Solution. | -        | -             |

### Product Info

| Range    | Supported Firmware |
|----------|--------------------|
| 1.0.0.0x | V1.20.03.02        |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to use

### General

The General page displays factory information of the device including the Serial Number, MAC Address, and Software Version.

Via the **Factory Info Tables** page button, you can view tables with additional device information such as System Names, Release Dates, Control Platform Versions, and more.

### System Data

The System Data page contains device KPIs like Battery Status, Total Output Current, SMR Voltage, etc.

### AC and DC Pages

The AC (Alternative Current) and DC (Direct Current) pages contain data specific to the respective current, including Voltage and Current tables.

### Environment Data

The Environment Data page displays the environment temperature.

### Alarms

On the Alarms page, you can adjust the severity of the alarms that are triggered if KPIs exceed certain thresholds.
