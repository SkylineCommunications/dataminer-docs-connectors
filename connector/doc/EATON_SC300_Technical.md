---
uid: Connector_help_EATON_SC300_Technical
---

# EATON SC300

## About

The SC300 System Controller is an advanced control and monitoring solution for the EATON Enterprise, Access, Metro, and Core Solutions.

The EATON SC300 connector can be used to monitor and control an EATON SC300 device. SNMP is used to communicate with the device. The information of the device is displayed on multiple pages, similar to the way it is displayed on the web interface of the device.

This connector is designed to be similar to the SC200 connector, which is used with the same family of SC devices.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **IP port**: The IP port of the destination (default: *161*).
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

On startup, the polling manager will automatically populate with suggested intervals to poll the different groups of parameters. You will need to define polling intervals and enable specific groups for polling according to your preferences.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector does not use the traditional timer threads to poll the SNMP groups from the device, but uses a priority buffer and a polling manager instead because of significantly long poll times for certain SNMP groups.

The element created with this connector consists of the data pages detailed below.

- **General**: Displays general information about the device, such as the **Location**, **Site Name**, and **Site Address**. Also contains a **Clock** section showing the **Controller Time**.

- **Identity**: Displays detailed identification information about the device, including the **System Manufacturer**, **System Serial Number**, **Type**, **Site Notes**, **Configuration Name**, **Configuration Hash**, **Configuration Modified**, **Site Building**, **Site Room**, **Site Contact**, **Site Support Contact**, and **Is Three Phase System**. A **Software** section is also available.

- **Communication - Remote Access Protocol**: Allows you to view and modify SNMP-related parameters such as **Trap Format** and **Generic Traps Enable**. A page button provides access to the **Trap Receiver Table**.

- **Alarm**: Displays alarm information across three sections: **Summary Alarms**, **Alarms Configuration**, and **Alarm States**.

- **Smart Alarm**: Displays the **Smart Alarm Table** with smart alarm data.

- **Smart Analog**: Displays the **Smart Analog Table** and **Smart Analog Mapping Table** with smart analog data.

- **Analog Input**: Displays information about the analog inputs in the **Analog Inputs** table. A page button provides access to the **Polling Config** subpage.

- **Digital Input**: Displays information about the digital inputs. A page button provides access to the **Polling Config** subpage.

- **Digital Output**: Displays information about the digital outputs. A page button provides access to the **Polling Config** subpage.

- **Rectifiers**: Allows you to view information and modify settings related to the rectifiers. Contains a **Rectifiers** section, a **Configuration** section, and a **Load Based Rectifier Shutdown** section. Page buttons provide access to the **Rectifier Values Table** and **Polling Config** subpages.

- **DCDC**: Allows you to view information and modify settings related to the DCDC converters.

- **Batteries**: Allows you to view information and modify settings related to the batteries. Contains a **Battery - Time Remaining** section, a **Midpoint Monitoring** section, and a **Battery Strings** section.

- **Polling Manager**: Displays the **Polling Queue** and allows you to configure polling intervals and enable or disable specific SNMP groups for polling.

- **Web Interface**: Displays the web interface of the device. The web interface is only accessible when the client machine has network access to the product.

## Notes

> [!IMPORTANT]
> The polling groups for the Smart Alarm table and Source Alarm table can take significantly longer than others.
