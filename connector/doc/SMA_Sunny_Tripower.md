---
uid: Connector_help_SMA_Sunny_Tripower
---

# SMA Sunny Tripower

## About

The SMA Sunny Tripower connector enables monitoring of the SMA Sunny Tripower linked to a solar environment via modbus. It provides users with access to real-time data directly within DataMiner.

## Key Features

- **Solar information**: Retrieve and monitor real-time active, apparent, reactive power information.
- **Performance monitoring and analysis**: Access analysis and monitoring data for all performance information linked to the solar enviroment.
- **Inverter Information**: Retrieve data from the inverter. This intales configuration and monitoring of the inverter unit.
- **Device Information**: Access and monitoring of the device configuration. 

## Technical Information

When you configure a DataMiner element using this connector, specify the IP address linked to the modbus and the port used to connect to the modbus (default: 502) and the slave ID needs to be placed in bussAddress (default:3).

Once an element is configured, the connector will automatically start polling data from the SMA Sunny Tripower.
