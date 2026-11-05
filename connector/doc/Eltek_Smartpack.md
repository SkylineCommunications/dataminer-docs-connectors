---
uid: Connector_help_Eltek_Smartpack
---

# Eltek Smartpack

The Eltek Smartpack is a controller that allows you to monitor and control DC power systems.

Information is polled from the device using SNMP calls. In addition, the original web interface of the device is available through the connector.

## About

### Version Info

| Range   | Key Features     | Based on | System Impact |
|---------|------------------|----------|---------------|
| 1.0.0.x | Initial version. | -        | -             |

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

#### SNMP main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector consists of different pages that cover the various subsections that can be monitored/controlled for this device. You can find more information on these below.

### General

This page displays general information about the device, such as the general **Status**, and power system information such as the **System Model**.

#### System Configuration

This page displays the general configuration of the device, such as the **Location** and the **Units** that are used.

#### Polling Manager

This page contains a polling table, which displays the polling state, interval, and last polled time, and contains a **Poll** button that can be used to manually trigger the polling.

### Mains

This page displays information about the mains, such as the **Mains Status** and **Mains Values**, as well as the **Mains Voltage Table**.

Via the **Configuration** page button, you can access related configurable parameters.

### Rectifiers

This page displays information about the rectifiers, such as the **Rectifiers Status** and **Rectifiers Values**.

The page contains a number of page buttons:

- **Configuration**: Provides access to all configurable parameters.
- **Energy Log**: Provides access to the energy logs tables.
- **Rectifiers**: Provides access to the rectifiers table.

### Load

This page displays information about the load, such as the **Load Status** and the **Load Values**.

The page contains a number of page buttons:

- **Configuration**: Provides access to all configurable parameters.
- **Energy Log**: Provides access to the energy logs tables.
- **Loads**: Provides access to the Group Table, LVLD Table, Fuse Table, and Voltage Table.

### Battery

This page presents details about the battery, including the **Battery Status** and **Battery Values**.

The page contains a number of page buttons:

- **Configuration**: Provides access to all configurable parameters.
- **Energy Log**: Provides access to the energy logs tables.
- **Cycle Log**: Provides access to the cycle logs tables.
- **Monitors**: Provides access to the battery monitors tables.
- **Banks**: Provides access to the battery banks tables.

### Battery Group 2

This page presents details about battery group 2, including the **Battery Group 2 Status** and **Battery Group 2 Values**.

The page contains a number of page buttons:

- **Configuration**: Provides access to all configurable parameters.
- **Energy Log**: Provides access to the energy logs tables.
- **Cycle Log**: Provides access to the cycle logs tables.
