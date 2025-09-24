---
uid: Connector_help_Frequentis_iRIF_Technical
---

# Frequentis iRIF

## About

The Frequentis iRIF is a IP-based radio gateway developed for safety- and mission-critical communications, particularly in air traffic management (ATM) and defense systems.

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

## How to use (1.0.0.x)

The connector consists of the following data pages:

- **General**: Displays general device information such as the system name and uptime.
If given high enough credentials (Group Level: 1), users can reboot the device or restart the application.
  - **Software**: This subpage displays available software images. 
	- If given high enough credentials (Group Level: 1), the table's rows can be right clicked on to open up a context menu. This context menu contains actions the user can perform on the software images.

- **Interfaces**: Displays a table containing useful metrics (In Bit Rate, Out Bit Rate etc) for device's interfaces. Users can also perform configurations on the interfaces.
- **Interfaces Details**: Displays tables containing rate information for the Rx and Tx components of the interfaces.
- **Sensors**: Displays sensor states.
  - **Temperature**: This subpage displays readings recorded from the temperature sensors.
  - **Fan**: This subpage displays the readings recorded from the fan sensors.
  - **PSU**: This subpage displays the readings recorded from the PSU sensors.
  - **CPU**: This subpage displays the readings recorded from the CPU sensors.
  - **HDD**: This subpage displays the readings recorded from the HDD sensors.

- **Service**: Displays software related services.
- **Hardware**: Displays hardware related info.
	- The tables' rows can be right clicked on to open up a context menu. These context menu contains actions the user can perform on the hardware module/interface.
- **Fourwire**: Displays fourwire related info.
- **Web Interface**: Displays the web interface of the polling IP address
