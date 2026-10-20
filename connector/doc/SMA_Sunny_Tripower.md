---
uid: Connector_help_SMA_Sunny_Tripower
---

# SMA Sunny Tripower

## About

The SMA Sunny Tripower connector monitors SMA Sunny Tripower inverters linked to solar environments via Modbus. It provides real-time data directly within DataMiner.

## Key Features

- **Solar information**: Retrieve and monitor real-time active, apparent, and reactive power information.
- **Performance monitoring and analysis**: Access analysis and monitoring data for all performance information linked to the solar environment.
- **Inverter information**: Retrieve inverter data, including configuration and monitoring information.
- **Device information**: Access and monitor the device configuration.

## Technical Reference

When you configure a DataMiner element using this connector, specify the IP address of the Modbus device, the port used to connect to the Modbus device (default: 502), and the slave ID. Set the slave ID in the busAddress field (default: 3).

Once an element is configured, the connector automatically starts polling data from the SMA Sunny Tripower.
