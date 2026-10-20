---
uid: Connector_help_Harmonic_NMX
---

# Harmonic NMX

## About

Harmonic's NMX Digital Service Manager is a video network management solution, encompassing a set of tools to monitor and manage Harmonic compressed digital video and audio systems.

The connector integrates with the NMX system to provide end-to-end visibility of compressed digital video and audio processing devices. It supports both legacy serial-based communication (XML SAPI) and modern REST API communication over HTTP and WebSocket.

## Key Features

- **Comprehensive alarm monitoring**: Collects alarms via SNMP polling, SNMP traps, and (from range 4.2.0.x onwards) real-time WebSocket notifications, providing immediate visibility into device health.

- **Dynamic Virtual Elements (DVEs)**: Automatically generates child elements per device and per switch, allowing operators to monitor individual hardware units in isolation with their own alarm and trending views.

- **Input and output service management**: Displays and manages input sources, services, streams, and output transports with full port-level enable/disable control.

- **Service plan monitoring**: Tracks service plans and their associated pools, SCGs, and DVBT2 configuration, giving operators full oversight of content delivery paths.

- **Redundancy group management**: Monitors primary and backup device states within redundancy groups and displays a tree control overview of switchover events, helping to ensure service continuity.

- **Flexible polling control**: Allows operators to selectively enable or disable port polling and configure additional polling for specific platform types to optimize network traffic.

## Use Cases

### Proactive Service Disruption Detection

**Challenge**: Video network operators need to detect and act on service disruptions before they affect end users, but managing hundreds of devices manually is impractical.

**Solution**: The connector centralizes alarm data from all NMX-managed devices in a single DataMiner element, combining SNMP traps and WebSocket notifications for near real-time alerting.

**Benefit**: Operators are notified immediately when a problem occurs, reducing mean time to repair and minimizing the impact of service disruptions.

### Multi-Device Management Through DVEs

**Challenge**: Large deployments may involve dozens of encoding, decoding, and switching devices managed through a single NMX system, making it difficult to assign per-device responsibility or to create device-specific dashboards.

**Solution**: The connector creates a separate dynamic virtual element for each device and switch, exposing per-device parameters, alarms, and input/output streams individually.

**Benefit**: Teams can assign monitoring responsibility per device, build targeted dashboards, and set up device-specific alarm thresholds without modifying the parent element.

### Redundancy Switchover Monitoring

**Challenge**: When a redundancy switchover occurs between primary and backup devices, operators need clear visibility into which device is currently active and whether the backup has taken over unexpectedly.

**Solution**: The Redundancy Overview page provides a tree control showing the active/standby status of every device in each redundancy group, updated automatically as switchovers occur.

**Benefit**: Operators can quickly identify unexpected failover switches, investigate root causes, and confirm that the system has returned to its primary configuration.

## Technical Reference

### Prerequisites

- **DataMiner 10.4.0.0** (Feature Release 14003) or higher is required.

- **Harmonic NMX firmware 8** or higher is required for ranges 4.1.0.x and later.

- A **dedicated API user account** on the NMX system is recommended for ranges 4.1.0.x and later.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Harmonic_NMX_Technical).
