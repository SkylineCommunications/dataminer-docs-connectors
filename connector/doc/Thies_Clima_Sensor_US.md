---
uid: Connector_help_Thies_Clima_Sensor_US
---

# Thies Clima Sensor US

The **Thies Clima Sensor US** is a weather station. It captures real-time information about wind, temperature, humidity, precipitation, pressure, brightness, and system status.

## About

Originally supporting a serial Modbus RTU implementation, the connector (from version 1.0.1.x) has been refactored to use **SNMP (v2c)**. The former Modbus-specific functionality and configuration workflow (e.g. switching device mode) have been removed.  
This connector now implements the **SNMP** interface only.

### Version Info

| Range            | Description                                                                 | DCF Integration | Cassandra Compliant |
|------------------|------------------------------------------------------------------------------|-----------------|---------------------|
| 1.0.0.x          | Initial version (Serial Modbus RTU implementation)                         | No              | Yes                 |
| 1.0.1.x [SLC Main] | Refactored to SNMP (v2c); removed Settings page; pruned & reordered parameters | No              | Yes                 |

### Product Info

| Range    | Supported Firmware Version |
|----------|----------------------------|
| 1.0.0.x  | 4.11                       |
| 1.0.1.x  | 4.11                       |

## Installation and configuration

### Creation

#### SNMP Main connection

As of version 1.0.1.x the connector uses an SNMP (v2c) connection.  
Provide the following during element creation:

SNMP CONNECTION:

- **IP address/host**: Device IP.
- **SNMP port**: Usually 161.

### Configuration

No protocol mode switching is required in the SNMP version. If upgrading from a prior (Modbus) deployment, remove any legacy Modbus-specific element instances and recreate them using SNMP.

## Usage

### General

This page shows system and status-related parameters:

- Sensor Status (raw bitfield source)
- PSU Voltage
- General Error
- Static Error
- Used Averaging Memory
- Plausibility Check
- Heating Release
- Heating Status

The General Error, Static Error, Averaging Memory usage, Plausibility, Heating Release, and Heating Status are decoded from the sensor status byte.

### Measurements

This page displays measurement groups:

- Wind: Mean Wind Speed, Wind Direction
- Humidity: Relative Humidity
- Precipitation: Precipitation Status, Precipitation Intensity, Precipitation Type
- Temperature: Air Temperature, Dew Point Temperature
- Pressure: Absolute Air Pressure, Relative Air Pressure
- Brightness: Brightness Highest Value

Examples include **Mean Wind Speed**, **Wind Direction**, **Relative Humidity**, **Precipitation Intensity**, **Precipitation Type**, **Air Temperature**, **Dew Point Temperature**, **Absolute Air Pressure**, **Relative Air Pressure**, and **Brightness Highest Value**.

### Settings

The Settings page has been removed in version 1.0.1.x (previous Modbus-specific configuration and mode switching are no longer applicable).