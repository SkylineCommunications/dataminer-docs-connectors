---
uid: Connector_help_NTI_ENVIROMUX_MINI_LXO
---

# NTI ENVIROMUX MINI LXO

The NTI ENVIROMUX MINI LXO is a device that helps with the monitoring of environmental conditions like temperature, water, humidity, and dry contact.

The NTI ENVIROMUX MINI LXO connector allows you to configure and monitor each of the sensors of the device. It aggregates the information from the different sensors in a single quick-access table with the most critical information of each sensor. It also provides a page for each sensor where you can view and configure the sensor details.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 2.9.2.r1.588       |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *public*).

## How to use

### General

This page displays the general information of the device including **DNS, Name, Location, IP, Mask, and Gateway**

### Overview

This page displays the **Summary** table, which contains critical information about the sensors, including:

- **Sensor Name**: The name configured on the device for the sensor.
- **Sensor Type**: The type of the sensor, i.e. *Temperature*, *Humidity*, *Dry Contact*, or *Water*.
- **Sensor Value (Reading)**: The current value read out from the sensor.
- **Sensor Status**: Indicates if the sensor is in alert state or not.

### Temperature (1, 2) Pages

These pages display information about the temperature sensors and allow you to configure them:

- **Temperature Current Value**: Displays the current value (sensor reading).
- **Temperature Alert**: Displays the current alert state (*On*/*Off*).
- **Temperature Sensor Name**: Allows you to view and edit the sensor name.
- **Temperature Sensor Unit**: Allows you to view and edit the sensor unit of measurement.
- **Temperature Sensor Low Threshold**: Allows you to view and edit the sensor low threshold. When the value is below this threshold, the sensor alert will be set to the value *On*.
- **Temperature Sensor High Threshold**: Allows you to view and edit the sensor high threshold. When the value is above this threshold, the sensor alert will be set to the value *On*.

### Humidity (1, 2) Pages

These pages display information about the humidity sensors and allow you to configure them:

- **Humidity Current Value**: Displays the current value (sensor reading).
- **Humidity Alert**: Displays the current alert state (*On*/*Off*).
- **Humidity Sensor Name**: Allows you to view and edit the sensor name.
- **Humidity Sensor Low Threshold**: Allows you to view and edit the sensor low threshold. When the value is below this threshold, the sensor alert will be set to the value *On*.
- **Humidity Sensor High Threshold**: Allows you to view and edit the sensor high threshold. When the value is above this threshold, the sensor alert will be set to the value *On*.

### Dry Contact (1, 2, 3, 4) Pages

These pages display information about the dry contact sensors and allow you to configure them:

- **Dry Contact Status**: Displays the current status (*Open*/*Closed*).
- **Dry Contact Alert**: Displays the current alert state (*On*/*Off*).
- **Dry Contact Sensor Name**: Allows you to view and edit the sensor name.
- **Dry Contact Sensor Alert Status**: Allows you to view and edit which value of the Dry Contact Status parameter will set the alert status to *On* or *Off*. This way, you can for example have the Dry Contact Alert set to *On* when the Dry Contact Status value is *Open*.

### Water Page

This page displays information about the water sensor and allows you to configure it:

- **Water Status**: Displays the current status (*Open*/*Closed*).
- **Water Alert**: Displays the current alert state (*On*/*Off*).
- **Water Sensor Name**: Allows you to view and edit the sensor name.
- **Water Sensor Alert Status**: Allows you to view and edit which value of the Water Status parameter will set the alert status to *On* or *Off*. This way, you can for example have the Water Alert set to *On* when the Water Status value is *Open*.

### Configuration

On this page, you can enable or disable the polling of each sensor.

Disabling the polling of a sensor will remove the sensor from the **Summary table** and will hide the corresponding page. Enabling the polling of a sensor will add the sensor to the **Summary table** and will show the page again.

By default, Temperature 2 Sensor and Humidity 2 Sensor are hidden.
