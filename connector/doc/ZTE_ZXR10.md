---
uid: Connector_help_ZTE_ZXR10
---

# ZTE ZXR10

## About

The ZTE ZXR10 connector enables integration with various models from the ZXR10 series. These carrier-grade devices are deployed in data center environments and support high-density network interfaces and advanced features such as VXLAN, SDN, MC-LAG, and Virtual Switch Clustering.

This connector uses SNMP to monitor the operational status and environmental conditions of ZXR10 switches, providing valuable insights into key hardware components such as interfaces, fans, power supplies, and temperature sensors.

## Key Features

- **Interface monitoring**: Displays the operational state of network interfaces across supported ZXR10 series switches.
- **Fan status**: Monitors the current status of all fans to ensure adequate system cooling.
- **Power supply monitoring**: Provides real-time information about power modules installed in the system.
- **Temperature tracking**: Reports temperature data from multiple modules for thermal monitoring.
- **Polling control**: Allows selective activation or deactivation of polling on specific data tables.

## Use Cases

### Use Case 1

**Challenge**: Real-time visibility on network switch performance and health in a distributed data center environment.

**Solution**: Use the ZXR10 connector to monitor interface status, temperature, fan activity, and power conditions.

**Benefit**: Early detection of hardware issues and improved response times for maintaining infrastructure availability.

### Use Case 2

**Challenge**: Managing multiple ZXR10 switch models within a single monitoring system.

**Solution**: Deploy the connector with SNMP integration to support different ZXR10 models under a unified view.

**Benefit**: Simplified operations and consistent data collection across hardware variations.

### Use Case 3

**Challenge**: Adjusting monitoring behavior based on specific operational requirements.

**Solution**: Use the Polling Control functionality to disable or enable certain tables according to system demands.

**Benefit**: Optimized system performance and monitoring efficiency.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to the [technical documentation](xref:Connector_help_ZTE_ZXR10_Technical).

