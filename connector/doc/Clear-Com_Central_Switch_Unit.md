---
uid: Connector_help_Clear-Com_Central_Switch_Unit
---

# Clear-Com Central Switch Unit

The CSU is a matrix to enable push-to-talk communication between network operators and customers.

This connector uses a serial connection to communicate with the device.

## About

### Version Info

| Range   | Description                                     | DCF Integration | Cassandra Compliant |
|---------|-------------------------------------------------|-----------------|---------------------|
| 1.0.0.x | Initial version.                                | No              | Yes                 |
| 1.1.0.X | Connector review; new features.                 | No              | Yes                 |
| 1.1.1.X | Minimum DataMiner version increased to 10.3.11. | No              | Yes                 |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | HCI 2.0            |
| 1.1.0.x | HCI 2.0            |
| 1.1.1.x | HCI 2.0            |

## Configuration

### Connections

#### Serial Connection — Main

This connector uses a serial-over-IP connection connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.

## Usage (1.0.0.x)

### General

This page displays general-purpose information such as **Master Uptime** and **Reset Flags**.

### Panel

On this page, you can fill in the necessary information to manually send a Key Panel Assignment command. It contains parameters such as **Card Number**, **Port Number**, **Destination Port**, **Key Number**, **Panel Type** (unused), and **Destination Type**.

### Crosspoints

This page contains a 512x512 **matrix**, which displays the current **crosspoints**.

### Configuration

On this page, you can configure the necessary information to send notifications to the manager element. The most important parameters are **DMA ID**, **Element ID**, **Other Parameter ID**, and a toggle button to enable or disable notifications.

## Usage (1.1.0.x)

### General

This page displays general-purpose information such as the status of the **CPU** and **Reset Flags**.

### Crosspoints

This page contains a 512x512 matrix, which displays the current **crosspoints**.

### Crosspoint Levels

This page displays the **crosspoints**, **inputs**, and **outputs** levels.

### Conferences

A tree control displays all the **Conferences** and the associated **Ports**. It is possible to add a new port to a conference and to set the type of the connection. You can also add or remove conferences.

### GPIO/SFO

This page displays the status of the **GPIO/SFO cards**.

### Panels

This page displays the status of the **panels** of the device.

### System Cards

This page displays the status of the **system cards** and the **system RCUs**.

### Alarms

This page displays the device alarms.

### Matrix

On this page, you can check the current matrix configuration.

## Usage (1.1.1.x)

### General

This page displays general-purpose information such as status of the **CPU** and **Reset Flags**.

### Configurations

On this page, you can change the configuration of the connector itself, e.g. **dynamic polling**.

### Crosspoints

This page contains a 512x512 matrix, which displays the current **crosspoints**.

### Crosspoint Levels

This page displays the **crosspoints**, **inputs**, and **outputs** levels.

### Conferences

A tree control displays all the **Conferences** and the associated **Ports**. It is possible to add a new port to a conference and to set the type of the connection. You can also add or remove conferences.

### GPIO/SFO

This page displays the status of the **GPIO/SFO cards**.

### Panels

This page displays the status of the **panels** of the device.

### System Cards

This page displays the status of the **system cards** and the **system RCUs**.

### Alarms

This page displays the device alarms.

### Matrix

On this page, you can check the current matrix configuration.
