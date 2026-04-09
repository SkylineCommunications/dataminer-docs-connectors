---
uid: Connector_help_AvL_Technologies_Intelligent_Terminal_Controller_Explorer
---

# AvL Technologies Intelligent Terminal Controller Explorer

## About

The AvL Technologies Intelligent Terminal Controller (ITC) Explorer connector enables seamless monitoring and management of satellite communication terminals via HTTP and WebSocket communication. It provides real-time visibility into antenna positioning, signal metrics, modem performance, alarms, and licensing information, allowing operators to maintain optimal system performance and quickly respond to issues.

## Key Features

- **Real-time WebSocket communication**: Ensures live updates of device parameters and statuses without polling delays.

- **Comprehensive antenna monitoring**: Tracks azimuth, elevation, polarization, and key RF metrics such as EIRP and G/T.

- **Advanced alarm handling**: Provides detailed fault and warning summaries for motors and transmit modules with root cause insights.

- **Multi-receiver visibility**: Monitors AVL, virtual, and power receivers including lock status, frequency, and signal strength.

- **Modem management**: Displays detailed modem information including signal strength, frequency, manufacturer, and software revision.

## Use Cases

### Satellite Terminal Monitoring

**Challenge**: Operators lack centralized visibility into antenna performance and RF metrics.

**Solution**: The connector aggregates all antenna and RF parameters into a single interface with real-time updates.

**Benefit**: Improved operational awareness and faster troubleshooting.

### Fault Detection and Diagnosis

**Challenge**: Identifying the root cause of antenna or transmission issues is time-consuming.

**Solution**: The connector provides detailed alarm summaries and reasons for each subsystem (motors, transmit modules).

**Benefit**: Reduced downtime and faster issue resolution.

### Network Performance Optimization

**Challenge**: Optimal signal quality must be maintained across multiple receivers and modems.

**Solution**: The connector allows continuous monitoring of signal strength, frequency, and lock status across all receiver and modem types.

**Benefit**: Enhanced signal reliability and improved service quality.

## Technical Reference

### Prerequisites

- **Network connectivity** is required to access the device via HTTP/WebSocket.

- **Valid credentials** are required for authentication.

- **WebSocket support** must be enabled on the device.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_AvL_Technologies_Intelligent_Terminal_Controller_Explorer_Technical).
