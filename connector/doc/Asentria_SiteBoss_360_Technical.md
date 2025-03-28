---
uid: Connector_help_Asentria_SiteBoss_360_Technical
---

# Asentria SiteBoss 360

## About

This connector is designed to monitor the Asentria SiteBoss 360 and connected Event Sensor Points.

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

## How to Use

### Event Sensor Points

The Event Sensor Points are separated by their types; i.e. Analog Inputs, Contact Closures, Humidity Sensors, Outputs, Temperature Sensors, with the monitoring and configuration tables on the same page.

In the Configuration table, each sensor point can be individually configured to change their states, thresholds, severities, and more dependent on the type of sensor point. For more information of each configurable parameter, refer to the corresponding information subtext.
