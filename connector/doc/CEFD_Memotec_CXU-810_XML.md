---
uid: Connector_help_CEFD_Memotec_CXU-810_XML
---

# CEFD MEMOTEC CXU-810

## About

The connector is used to configure and monitor a CXU-810. It uses SNMP and a DLL to communicate with the device.

## Configuration

### Prior to Element Creation

Before you will be able to use the connector, you will need to copy two DLL files ("**cxcuaconfigapi_SLC.dll**" and "**cxuaconfigapi.dll**" ) to the following location:**"C:\Skyline DataMiner\Files"**

Also make sure that the device is running at **firmware version 2.9.0** or higher.

### Connections

Once you have taken care of the configuration above, you can create an element with this connector using the following settings:

**SNMP CONNECTION**:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*
- **Device address**: the card number eg. 11

**SNMP Settings**:

- **Port number**: the port of the connected device, default *161*
- **Get community string**: the community string in order to read from the device. The default value is *public*.
- **Set community string**: the community string in order to set to the device. The default value is *private.*

## Usage

Once all configuration is done, this connector will work standalone.

All settings done in DataMiner will be done to the **pending configuration** of the device and will then have to be applied.

## General Page

This page contains some general data concerning the device.

## Admin Page

This page contains standard administrator parameters such as the location and name of the device.

There are also buttons to reset the device or reboot it with the alternate firmware, as well as options to set the trap receiver IP and the redundancy.

You can also **validate the pending configuration** here and **apply** this configuration to the running configuration of the device.

## Configuration - Network Page

On this page, you will find the configuration of the Management interface and the WAN interface.

To apply the new settings to the device, you can use the apply configuration button located at the bottom of the page.

> [!IMPORTANT]
> When the apply configuration button is clicked, all settings of the connector will be applied to the running configuration and not only those of the Configuration - Network page.

## Configuration - E1 Ports Page

On this page, you will find the settings of the E1 ports and the optimization.

To apply the new settings to the device, you can use the apply configuration button located at the bottom of the page

> [!IMPORTANT]
> When the apply configuration button is clicked, all settings of the connector will be applied to the running configuration and not only those of the Configuration- E1 Ports page.

## Configuration - Wan interfaces Page

On this page, you will find the configuration of the WAN Interfaces and the Bandwidth Provider.

To apply the new settings to the device, you can use the apply configuration button located at the bottom of the page.

> [!IMPORTANT]
> When the apply configuration button is clicked, all settings of the connector will be applied to the running configuration and not only those of the Configuration- Wan interfaces page.

## Configuration - Clocking

On this page, you will find the Clocking Configuration.

Via the page button **E1 Ports**, you can check the state of the different E1 ports.

## Statistics - Network

This page shows the stats of the network interface.

With the clear button, you can clear all the statistics of the device.

## Statistics - E1 Ports

This page shows the stats of theE1 ports.

With the clear button, you can clear all the statistics of the device.

## Statistics - Wan Interfaces

This page shows the stats of the WAN interfaces.

With the clear button, you can clear all the statistics of the device.

## Statistics - Clocking

This page shows the stats of the clocking of the device.

With the clear button, you can clear all the statistics of the device.

## Statistics - Optimization

This page shows the stats of the optimization of the device.

With the clear button, you can clear all the statistics of the device.

When you click the button "select E1 Port", the E1 port will be selected for the displaying of the timeslot formats located under the Mapping Page button. When no button is clicked before the page is opened, this will by default be port 1.

## Alarms

This page contains a table listing the currently active alarms and the alarm history of the device.

There is also a global alarm severity of the device available.

The clear button located at the bottom of the page is used to clear the active alarms.

Via the page button **Alarm Management**, you can acknowledge an alarm.

## Test Commands

On this page, you can get the raw XML data from the device.

This is done in 2 steps:

- Fill in the URL of the XML to get in the parameter "**XML Path"**.
- Click the Get button. This will then get XML from the device and put it in the XML Answer Textbox.

## Web interface

On this page, you will find the web interface of the device.
