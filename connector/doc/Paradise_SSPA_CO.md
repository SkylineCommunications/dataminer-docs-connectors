---
uid: Connector_help_Paradise_SSPA_CO
---

# Paradise SSPA CO

## About

The **Paradise SSPA CO** connector enables monitoring and control of Paradise Compact Outdoor Solid-State Power Amplifiers (SSPAs) via serial communication. The connector provides visibility on key amplifier metrics, health indicators, and operational configuration, helping satellite operators maintain high uplink performance.

## Key Features

- **RF performance monitoring**: Displays forward and reflected RF power, along with attenuation settings.
- **Electrical and thermal metrics**: Tracks temperature, SSPA current, and internal voltages.
- **Fault detection**: Shows alarms for high temperature, low current, BUC issues, and more.
- **Configurable fault logic**: Allows the setup of logic and handling behavior for auxiliary and spare fault types.
- **Amplifier control**: Supports remote control of attenuation, mute, calibration, and standby modes.

## Use Cases

### Use Case 1

**Challenge**: Operators need to monitor power amplifier performance and environmental metrics remotely in remote uplink facilities.

**Solution**: The connector polls the SSPA for RF power levels, temperature, voltage, and current, displaying it clearly on the System Info page.

**Benefit**: Enables proactive maintenance and quick detection of issues before signal degradation occurs.

### Use Case 2

**Challenge**: Fault conditions often go undetected until service impact occurs, making troubleshooting reactive and slow.

**Solution**: The connector detects and alarms on conditions like over-temperature, low voltage, and BUC faults, with configurable fault thresholds and logic.

**Benefit**: Provides real-time alerts and helps engineers configure appropriate fault handling strategies to reduce downtime.

## Technical Reference

### Prerequisites

- **Minimum required DataMiner version**: 10.3.0

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Paradise_SSPA_CO_Technical).
