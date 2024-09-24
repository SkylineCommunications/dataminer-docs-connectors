---
uid: Connector_help_Junger_TAP
---

# Junger TAP

The **Junger TAP** is a sophisticated audio processor, powered by Analog Devices Sharc DSPs. These DSPs provide the 10-channel audio processing and monitoring facility. They are surrounded by several I/O interfaces, audio delay lines and an optional Dolby decoder and encoder.

## About

This connector uses an **SNMP** connection (and a smart-serial connection for [Ember+](https://github.com/Lawo/ember-plus/wiki) in range 1.0.1.x) to communicate with the device.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| 1.0.0.x | Initial version | No | Yes |
| 1.0.1.x | Based on 1.0.0.1 Added hotkeys and network triggers by creating a smart-serial connection for the [Ember+](https://github.com/Lawo/ember-plus/wiki) protocol. Element settings must be adjusted when updating to this version. | No | Yes |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | 2.0.40                      |
| 1.0.1.x          | 2.0.40                      |

## Configuration

### Connections - Range 1.0.0.x

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Connections - Range 1.0.1.x

> [!NOTE]
> When you update from version 1.0.0.x to 1.0.1.x, you must adjust the element settings.

#### Smart-Serial Connection - Main

This connector uses a smart-serial connection to be able to use the [Ember Plus Protocol](https://github.com/Lawo/ember-plus/wiki) for communication with the device.

SMART-SERIAL CONNECTION:

- **IP address/host**: The polling IP of the device.

SMART-SERIAL Settings:

- **IP Port:** The port of the device. The default port for this serial connection is port *9000*.

#### SNMP Connection - Second

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

## Usage

### General

This page displays general information about the device, such as the **System description**, **System Uptime** and **General Status.**

### Status

This page displays status information, such as the **Temperature**, **Power** and **Fan Status**, **NTP** and **Number of Modules**.

### Module

This page provides information about the various module entries.

### Input

This page displays status information regarding the interface module.

### Process

This page displays information related to the **Processing Status** of each module.

### Session

This page shows the available **Sessions.**

### Hotkeys

From version 1.0.1.1 onwards, you can activate the hotkeys and network triggers by clicking the **Trigger** button.

Note that changing the label of a hotkey will also trigger the hotkey.

### Web Interface

This page displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
