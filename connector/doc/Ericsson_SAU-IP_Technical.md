---
uid: Connector_help_Ericsson_SAU-IP_Technical
---

# Ericsson SAU-IP

This connector monitors the Ericsson Service Access Unit (SAU).

## About

### Version Info

| Range              | Key Features                                                                                      | Based on | System Impact |
|--------------------|---------------------------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version.                                                                                  | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -		                 |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection - [Name of the connection]

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]

SNMP Settings:

- **Port number**: [The port of the connected device, by default 161.]
- **Get community string**: [The community string used when reading values from the device (default: *public*).]
- **Set community string**: [The community string used when setting values on the device (default: *private*).]

## How to use

### Input Alarm Configuration
These settings can be accessed on the Inputs page.
- **Name**: This parameter can be set to provide a better description of what the sensor is monitoring.

- **State**: This parameter toggles between enabling and disabling the alarm for the row item. Disabling an enabled alarm will also clear the existing alarm, if any.

- **Configuration**: This parameter refers to the default state of the monitored Input; a Normally Closed Input will trigger an alarm when it opens and vice versa

- **Severity**: This parameter is a configuration parameter that allows the user to set the severity of the resultant alarm for the associated Input.

When an Input alarm is activated, it will be indicated as 'Active' in the **Status** column. This alarm will also be represented on the Alarms table.
The user can choose which location (Alarm table or Inputs table) to alarm on, noting that alarming on both locations will result in duplicate alarms for the same incident.

### Output Alarm Configuration
These settings can be accessed on the Outputs page.
- **Name**: This parameter can be set to provide a better description of what the sensor is monitoring.

- **State**: This parameter toggles between enabling and disabling the alarm for the row item. Disabling an enabled alarm will also clear the existing alarm, if any.

- **Severity**: This parameter is a configuration parameter that allows the user to set the severity of the resultant alarm for the associated Input.

- **Status**: As an output parameter, the status can be manually toggled between Alarm and No Alarm states. To make a valid remote set from this connector/device to the sensor, the **State** should be Enabled and **Severity** should be Remote.

