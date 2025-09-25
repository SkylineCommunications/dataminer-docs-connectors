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

### General Page

This page displays general device information such as the system name and uptime.

If given high enough credentials (group level: 1), you can also reboot the device or restart the application.

On the **Software** subpage, you can find the available software images. If given high enough credentials (group level: 1), you can right-click a row in the table to access a context menu that allows you to perform actions on the software images.

### Interfaces Page

This page displays a table containing useful metrics (In Bit Rate, Out Bit Rate, etc.) for the interfaces fo the device. You can also configure settings of the interfaces.

### Interfaces Details Page

This page displays tables containing rate information for the Rx and Tx components of the interfaces.

### Sensors Page

This page displays sensor states. In addition, it has the following subpages:

- **Temperature**: This subpage displays readings recorded from the temperature sensors.
- **Fan**: This subpage displays the readings recorded from the fan sensors.
- **PSU**: This subpage displays the readings recorded from the PSU sensors.
- **CPU**: This subpage displays the readings recorded from the CPU sensors.
- **HDD**: This subpage displays the readings recorded from the HDD sensors.

### Service Page

This page displays software-related services.

### Hardware Page

This page displays hardware-related info.

You can right-click the rows in the tables to open a context menu that allows you to perform actions on the relevant hardware module or interface.

### Fourwire Page

This page displays fourwire-related info.

### Web Interface Page

This page displays the web interface of the polling IP address. It is only available when the client machine has network access to the product.
