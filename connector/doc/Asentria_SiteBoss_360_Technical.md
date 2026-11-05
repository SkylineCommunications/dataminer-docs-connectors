---
uid: Connector_help_Asentria_SiteBoss_360_Technical
---

# Asentria SiteBoss 360

## About

This connector is designed to monitor the Asentria SiteBoss 360 and connected event sensor points.

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

The connector has dedicated pages with monitoring and configuration tables for each of the different types of event sensor points: Analog Inputs, Contact Closures, Humidity Sensors, Outputs, and Temperature Sensors.

In the configuration tables, each sensor point can be individually configured to change its states, thresholds, severities, and more, depending on the type of sensor point. For more information about each configurable parameter, refer to the information displayed for the parameter in DataMiner.
