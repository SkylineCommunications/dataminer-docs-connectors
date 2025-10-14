---
uid: Connector_help_Frequentis_iRIF_Technical
---

# Frequentis iRIF

## About

The Frequentis iRIF is an IP-based radio gateway developed for safety- and mission-critical communications, particularly in air traffic management (ATM) and defense systems.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection to process incoming traps. It requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: By default *161*.
- **Get community string**: The community string used when reading values, by default *public*.
- **Set community string**: The community string used when setting values, by default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use (Range 1.0.0.x)

### General

This page displays general device information such as the system name and uptime.

If given high enough credentials (group level: 1), you can also reboot the device or restart the application.

On the **Software** subpage, you can find the available software images. If given high enough credentials (group level: 1), you can right-click a row in the table to access a context menu that allows you to perform actions on the software images.

### Interfaces

This page displays a table containing useful metrics (In Bit Rate, Out Bit Rate, etc.) for the interfaces fo the device. You can also configure settings of the interfaces.

### Interface Details

This page displays tables containing rate information for the Rx and Tx components of the interfaces.

### Hardware

This page displays hardware-related info.

You can right-click the rows in the tables to open a context menu that allows you to perform actions on the relevant hardware modules.

### Hardware Interfaces

This page displays a table of hardware interfaces.

You can right-click the rows in the tables to open a context menu that allows you to perform actions on the relevant hardware interfaces.

### Temperature

This page displays temperature readings across the device.

### Fan

This page displays fan readings across the device.

### PSU

This page displays PSU readings across the device.

### CPU

This page displays CPU readings across the device.

### HDD

This page displays HDD readings across the device.

### Four-wire

This page displays a table of four-wire codec lines.

### Service

This page displays software-related services.

You can right-click the rows in the tables to open a context menu that allows you to perform actions on the relevant services.

### Service Alarms

This page displays alarms related to the services.

### Web Interface Page

This page displays the web interface of the polling IP address. It is only available when the client machine has network access to the product.