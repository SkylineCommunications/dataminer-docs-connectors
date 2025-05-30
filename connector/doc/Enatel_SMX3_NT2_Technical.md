---
uid: Connector_help_Enatel_SMX3_NT2_Technical
---

# Enatel SMX3 NT2

The Enatel SM3X series are supervisory modules that provide control and monitoring for power systems, including rectifiers, converters, and inverters. They monitor system conditions, log data, and offer local and remote alarm notifications and configuration capabilities.
The Enatel SMX3 NT2 connecto helps centralizing all the information into a single source with sections provided for each category of information, offering options to change device settings directly from the connector.

## About

### Version Info


|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |<ul><li>SM32 NT2</li><li>SM34 NT2</li><li>SM36 NT2</li></ul>         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device. (default: *public*)
- **Set community string**: The community string used when setting values on the device. (default: *private*)


### Initialization

No additional initialization is needed in order to get the connector running.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General Page

This page contains the general system information about the device

### Currents Page

This page contains 3 subpages with information about current and voltage

#### AC 1/2

These pages contain the voltage, current and frequency information for the Alternating Currents.

#### DC

This page contains information for the converter, rectifier and battery such as voltage, current and battery capacity

### Rectifiers

This page contains information about the number of communicating rectifiers, it also allows the user to enable power save and temperature compensation.

### Battery

This page contains information and settings for the battery, such as battery levels, voltage, current, power saving and testing.

### Alarm Thresholds

This page contains the subpages for all the configurable thresholds for alarms for the different components of the system such as **current**, **temperature**, **alternating current**, **voltage**, **lvd**.

### Power Modules

This page contains the Power Modules table with information for the power modules available in the device, also allows the user to shutdown the modules.