---
uid: Connector_help_Paradise_SSPA_CO
---

# Paradise SSPA CO

## About

The **Paradise SSPA CO** connector enables monitoring and control of Paradise Compact Outdoor Solid-State Power Amplifiers (SSPAs) via serial communication. The connector provides visibility into key amplifier metrics, health indicators, and operational configuration, helping satellite operators maintain high uplink performance.

## Key Features

- **RF Performance Monitoring**: Displays forward and reflected RF power, along with attenuation settings.
- **Electrical & Thermal Metrics**: Tracks temperature, SSPA current, and internal voltages.
- **Fault Detection**: Alarms for high temperature, low current, BUC issues, and more.
- **Configurable Fault Logic**: Setup logic and handling behavior for auxiliary and spare fault types.
- **Amplifier Control**: Supports remote control of attenuation, mute, calibration, and standby modes.

## Use Cases

### Use Case 1

**Challenge**: Operators need to monitor power amplifier performance and environmental metrics remotely in remote uplink facilities.

**Solution**: The connector polls the SSPA for RF power levels, temperature, voltage, and current, displaying it clearly in the System Info page.

**Benefit**: Enables proactive maintenance and quick detection of issues before signal degradation occurs.

### Use Case 2

**Challenge**: Fault conditions often go undetected until service impact occurs, making troubleshooting reactive and slow.

**Solution**: The connector detects and alarms on conditions like over-temperature, low voltage, and BUC faults, with configurable fault thresholds and logic.

**Benefit**: Provides real-time alerts and helps engineers configure appropriate fault handling strategies to reduce downtime.

## Technical Reference

### Prerequisites

- **TCP/IP Communication** with access to the device's IP and port.
- **Bus Address** must be known and within 0–31 range.
- **Device Compatibility**: Paradise Compact Outdoor Solid-State Power Amplifiers.
- **Minimum Required DataMiner Version**: 10.3.0.0-12752 or higher

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Paradise_SSPA_CO_Technical).
