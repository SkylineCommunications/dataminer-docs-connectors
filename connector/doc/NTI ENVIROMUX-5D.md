---
uid: Connector_help_NTI_ENVIROMUX_5D
---

# NTI ENVIROMUX-5D

## About

This connector uses SNMPv2 communication to monitor the NTI ENVIROMUX-5D Enterprise Environment Monitoring System. It retrieves data from internal temperature and humidity sensors, up to five external configurable sensors, digital inputs, IP devices, output relays, and power supplies. It also provides smart alert management, network configuration visibility, and access to extended sensor types such as TAC, IP, and auxiliary sensors.

## Key Features

- **Environmental sensor monitoring**:

  - Real-time readings from internal temperature and humidity sensors.
  - Support for up to five external configurable sensors (temperature, humidity, dew point, power, and more) with threshold and warning level tracking.
  - Auxiliary, TAC, and IP sensor support for extended deployment scenarios.
  - Aggregated view of all external sensors in a single unified table.

- **Power and infrastructure monitoring**:

  - Power supply status monitoring for dual-feed environments.
  - Output relay status and control for external device actuation.
  - Digital input monitoring with configurable normal-state tracking.

- **Alert and event management**:

  - Smart alerts with configurable threshold-based triggers.
  - Event log visibility for tracking alert history and status changes.
  - Smoke detector, siren beacon, and message register monitoring.

- **Network and remote management**:

  - IPv4, IPv6, and VLAN network configuration visibility.
  - Remote input and relay monitoring for cascaded unit deployments.
  - Embedded web interface access directly from the DataMiner element.

## Use Cases

### Data Center Environmental Compliance Monitoring

**Challenge**: Data centers must maintain temperature and humidity within strict operating ranges to protect equipment and meet compliance requirements.

**Solution**: The connector continuously polls internal and external sensors, comparing readings against configurable min/max and warning thresholds.

**Benefit**: Enables proactive alerting before environmental conditions reach critical levels, supporting SLA compliance and reducing the risk of heat-related equipment failures.

### Power and Infrastructure Event Detection

**Challenge**: Power anomalies such as voltage spikes, sags, or current swells can go undetected until equipment fails.

**Solution**: The External Sensors ACLM table captures peak values, frequency, current, spikes, swells, and sags for power-type sensors, providing detailed AC line monitoring data.

**Benefit**: Allows NOC teams to correlate environmental events with equipment behavior and take corrective action before failures occur.

### Multi-Site Remote Monitoring

**Challenge**: Organizations managing multiple sites need centralized visibility into distributed environmental monitoring units without on-site presence.

**Solution**: The connector exposes IP device reachability, remote input/relay state, and all sensor data via SNMP polling into DataMiner, enabling centralized dashboards and alarm workflows.

**Benefit**: Reduces the need for on-site visits and enables faster response to environmental incidents across distributed infrastructure.

### Physical Security and Intrusion Detection Integration

**Challenge**: Digital contact sensors for door monitoring and smoke detectors need to be integrated into a unified monitoring platform alongside environmental data.

**Solution**: The connector monitors digital inputs, smoke detectors, and remote relay states alongside temperature, humidity, and power sensors in a single DataMiner element.

**Benefit**: Provides a consolidated physical security and environmental monitoring view, simplifying incident correlation and escalation workflows.

## Technical Reference

> [!NOTE]
> For setup and configuration instructions, refer to the [technical documentation](xref:Connector_help_NTI_ENVIROMUX_5D_Technical).