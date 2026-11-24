---
uid: Connector_help_Inrow_Fiberhome_Technical
---

# Inrow Fiberhome

## About

This connector communicates with the Inrow Fiberhome in-row cooling unit over SNMP. It monitors unit operation, environmental readings, alarms, and equipment status. The **Settings** page also exposes supported read/write controls and setpoints.

## Configuration

### Connections

#### SNMP Connection

The protocol uses SNMPv2. Configure an SNMP connection to the device when creating the element:

- **IP address/host**: The management address of the device.
- **IP port**: The SNMP destination port. The connector definition does not specify a connector-specific port default.
- **Bus address**: Configure the address required by the element's SNMP connection settings.
- **SNMP community strings**: Provide credentials with read access for monitoring. Write access is required for the connector's read/write settings. The protocol does not define community-string defaults.

The connector definition does not specify additional connection types or explicit port or bus-address defaults.

## How to Use

The pages below organize device details by function. Values displayed depend on the data exposed by the device through its SNMP agent.

### General

Shows standard SNMP system information, including the system description, uptime, contact, name, and location.

### Settings

Use this page to review and, where exposed as read/write controls, change device settings. These include return-, supply-, and remote-temperature setpoints; humidity and high/low temperature and humidity alarm setpoints; device state; local operation; and delayed start. Group-related settings include temperature/humidity control mode, group/network operation, communication addresses, group and backup unit counts, unit rotation mode and cycle, feedback parameter type, and selected operating options.

Only parameters defined as writable by the connector can be set. Whether a change is accepted depends on the device and the SNMP credentials.

### System

Contains system operating settings and two tables:

- **System**: Indexed system records, including the unit's system values and readings.
- **Electricity**: Indexed daily electricity values, reported in kWh by the connector.

### Fan

The **Fan** table lists indexed fans and their speed-feedback fault status, displayed as **Normal** or **Fault**.

### Indoor Unit

Shows indoor-unit state and operating mode, together with indoor, supply-air, and return-air temperature and humidity readings. It also exposes running-time counters, supply voltage, fan speeds, and other unit operating values.

### Outdoor Unit

Shows outdoor-unit fault and maintenance indicators, including humidifier overrun, condensate high-water protection, filter maintenance, ammeter communication, and Power B status. The **Outdoor Unit** table provides indexed outdoor-unit readings, including water temperature and fan speed, alongside status values.

### Sensors

Shows sensor and environmental alarms, including high/low temperature and humidity, supply-air temperature limits, return- and supply-air sensor faults, drainage, and differential air-pressure sensor status. Alarm states are represented as **Normal** or **Fault** where defined by the connector.

### Cabinet

Contains two indexed tables:

- **Cabinet Air Supply Exp**: Cabinet temperature and humidity and temperature/humidity sensor fault status.
- **Pump Cabinet**: Pump-cabinet information, including fluorine pump speed and available pump status values.
