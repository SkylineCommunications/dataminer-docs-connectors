---
uid: Connector_help_Imagine_Communications_Selenio_FR3
---

# Imagine Communications Selenio FR3

The **Imagine Communications Selenio FR3** is the default controller card slotted into a Selenio chassis at position 0. This connector lists the important parameters of this controller and provides an overview of all the different slots in the chassis.

## About

The information displayed in this connector is delivered on different pages, described in the **Usage** section of this document.

The **versioning** for the connector is specifically engineered to tie in with the firmware version of the card the connector supports. It uses the following format: X.X.X.Y, with X.X.X being the firmware version of the card and .Y the specific connector iteration for this firmware. For example, *5.0.28.2* means the connector is the second iteration for firmware *5.0.28.*

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| \<10.0.0.x [SLC Main] | The **versioning** of the connector is specifically engineered to tie in with the firmware version of the card the connector supports. | No | Yes |
| 10.0.0.x | Replaced the "dynamic snmp get" with "dynamicSnmpGet="true"" under parameter type tag. | No | Yes |

### Product Info

| Range | Device Firmware Version |
|--|--|
| \<10.0.0.x [SLC Main] | The **versioning** of the connector is specifically engineered to tie in with the firmware version of the card the connector supports. |
| 10.0.0.x | Requires controller firmware "S/W=7.0-38, H/W= rev 02" or higher and will not work with older firmware. |

## Installation and configuration

### Creation

#### SNMP main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: This is always 0. As such, it cannot be modified during element creation.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string needed to read from the device. The default value is *public*.
- **Set community string**: The community string needed to set to the device. The default value is *public.*

### Timing

All data gets retrieved from the device in three ways.

1. **Timers**

   - Slow timer that triggers every hour and retrieves non-essential and configurable parameters.
   - Medium timer that triggers every 10 minutes and retrieves status parameters and the connections table.
   - Alarm slow timer that triggers every 30 seconds and retrieves alarm information (see note below).
   - Fast timer that triggers every 10 seconds and retrieves slot information (state, temperature, protection, etc.).
   - Very fast timer that triggers every 3 seconds and retrieves dirty changes, alarm information (see note below) and CPU polling if enabled.

1. **Dirty changes**

   - Every 3 seconds, a check is done for any changed configurable values. If such a change is detected, the new value is retrieved and instantly updated in the element. If the change is the cell of a table, the complete table is refreshed. After a change is detected, the check is boosted and performed every 0.5 seconds, until no more changes are detected.

1. **Traps**

   - When enabled and set up on the controller, traps can be sent to DataMiner whenever an alarm occurs. The traps are accepted and processed for the controller.

> [!NOTE]
> You can toggle alarm information to be retrieved either every 30 seconds or every 3 seconds. The default value is every 3 seconds. It is recommended not to change this to 30 seconds unless you enable traps to be sent to DataMiner.

## Usage

The connector consists of the pages and sections described below.

### General Page

This page contains version information and controller status parameters.

The **Processor Usage** page button can be used to monitor the total CPU % of the chassis. Polling for this is disabled by default but can be toggled on.

### Alarming Page

This page lists all possible alarms for the controller. If an alarm is active, the **Controller Alarm State** will indicate what kind of alarm it is.

The page contains a toggle button that allows you to change alarm polling speed to 3 or 30 seconds. It is recommended to set up traps and reduce the polling speed to 30s.

### Slot Table Page

This page provides an overview of all slots in the chassis and the cards plugged in at those positions, if any.

It also provides access to the **Failover** and **Failback** configuration, and allows you to configure the **Slot Protection** and **Reboot** possibilities.

### Connections Page

On this page, the **Connections** table provides a complete overview of all internal connections made in the chassis. The table displays **interface data**, **slot data** and **services** running.

With the **Add Connection** page button, you can add additional connections. You can clean invalid connections from the table with the **Remove Invalids** button.

### General Section

This section contains information concerning the internal **Modules**, **Reference** and **TSG**.

It also allows you to upload certain system-stored **Presets**.

### Control Section

This section contains parameters to enable or disable certain communication protocols such as **SNMP**, **FTP**, **HTTP**, **SSH**, **CCSP** and **Telnet.** It also contains three pages for specialized **SNMP**, **GPI** or **Ethernet** settings.

### Redundancy Section

This section contains the **Router** page, which contains all information concerning 15 different **Levels** in the router.
