---
uid: Connector_help_ZTE_ZXR10
---

# ZTE ZXR10 Connector

## About

The ZTE ZXR10 connector enables integration with various models from the ZXR10 series. These carrier-grade devices are deployed in data center environments and support high-density network interfaces and advanced features such as VXLAN, SDN, MC-LAG, and Virtual Switch Clustering.

This connector uses SNMP to monitor the operational status and environmental conditions of ZXR10 switches, providing valuable insights into key hardware components such as interfaces, fans, power supplies, and temperature sensors.

## Key Features

- **Interface Monitoring**: Displays the operational state of network interfaces across supported ZXR10 series switches.
- **Fan Status**: Monitors the current status of all fans to ensure adequate system cooling.
- **Power Supply Monitoring**: Provides real-time information about power modules installed in the system.
- **Temperature Tracking**: Reports temperature data from multiple modules for thermal monitoring.
- **Polling Control**: Allows selective activation or deactivation of polling on specific data tables.

## Use Cases

### Use Case 1

**Challenge**: Need for real-time visibility into network switch performance and health in a distributed data center environment.

**Solution**: Use the ZXR10 connector to monitor interface status, temperature, fan activity, and power conditions.

**Benefit**: Early detection of hardware issues and improved response times for maintaining infrastructure availability.

### Use Case 2

**Challenge**: Managing multiple ZXR10 switch models within a single monitoring system.

**Solution**: Deploy the connector with SNMP integration to support different ZXR10 models under a unified view.

**Benefit**: Simplified operations and consistent data collection across hardware variations.

### Use Case 3

**Challenge**: Need to adjust monitoring behavior based on specific operational requirements.

**Solution**: Use the Polling Control functionality to disable or enable certain tables according to system demands.

**Benefit**: Optimized system performance and monitoring efficiency.

## Technical Reference

### Prerequisites

- Any **ZXR10 switch** running supported firmware (e.g., V5.00.00R6P99).
- **SNMP access** with appropriate community strings (default: `public` for GET, `private` for SET).
- **Polling IP address and port** of the device.
- **Bus address** of the device, if required.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_ZTE_ZXR10_Technical).
