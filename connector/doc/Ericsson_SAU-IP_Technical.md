---
uid: Connector_help_Ericsson_SAU-IP_Technical
---

# Ericsson SAU-IP

## About

This connector monitors the Ericsson Service Access Unit (SAU).

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.

SNMP Settings:

- **Port number**: The port of the connected device, by default 161.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to use

### Input Alarm Configuration

These settings can be accessed on the **Inputs** page.

- **Name**: This parameter can be set to provide a better description of what the sensor is monitoring.

- **State**: This parameter toggles between enabling and disabling the alarm for the row item. Disabling an enabled alarm will also clear the existing alarm, if any.

- **Configuration**: This parameter refers to the default state of the monitored input. A "Normally Closed" input will trigger an alarm when it opens and vice versa.

- **Severity**: This configuration parameter allows you to set the severity of the resulting alarm for the associated input.

When an Input alarm is activated, it will be indicated as 'Active' in the **Status** column. This alarm will also be represented on the Alarms table.
The user can choose which location (Alarm table or Inputs table) to alarm on, noting that alarming on both locations will result in duplicate alarms for the same incident.

### Output Alarm Configuration

These settings can be accessed on the **Outputs** page.

- **Name**: This parameter can be set to provide a better description of what the sensor is monitoring.

- **State**: This parameter toggles between enabling and disabling the alarm for the row item. Disabling an enabled alarm will also clear the existing alarm, if any.

- **Severity**: This configuration parameter allows you to set the severity of the resulting alarm for the associated output.

- **Status**: For an output parameter, you can manually toggle the status between *Alarm* and *No Alarm*. To make a valid remote set from this connector to the sensor, the **State** has to be set to *Enabled* and the **Severity** has to be set to *Remote*.
