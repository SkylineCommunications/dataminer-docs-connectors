---
uid: Connector_help_AvL_Technologies_AAQ_Controller
---

# AvL Technologies AAQ Controller

## About

The AvL Technologies AAQ Controller connector is designed for DataMiner integration with AvL Technologies' Antenna Acquisition and Pointing (AAQ) systems. It provides SNMPv2-based access to system state, axis positions, motor and limit switch status, and GPS data, supporting comprehensive remote monitoring.

## Key Features

- **SNMPv2-based monitoring**: Real-time polling of all relevant device parameters.
- **Comprehensive status pages**: System, Azimuth, Elevation, Polarity, Wing, and GPS.
- **Automatic alarm generation**: Alarms based on parameter thresholds and status values.

## Use Cases

### Use Case 1: Remote Antenna Health Monitoring

**Challenge**: Ensuring continuous operational status of remote antennas.
**Solution**: Use the connector to monitor system state, motor health, and limit switches in real time.
**Benefit**: Early detection of faults and reduced downtime.

### Use Case 2: Automated Safety and Positioning

**Challenge**: Preventing mechanical damage due to limit violations.
**Solution**: Monitor and alarm on stow positions and limit switch activations.
**Benefit**: Improved safety and reduced risk of hardware failure.

## Technical Reference

### Prerequisites

- DataMiner version 10.3.0.0 - 12752 or higher.
- AvL Technologies AAQ Controller firmware 2.9.2.r1.588 or higher.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_AvL_Technologies_AAQ_Controller_Technical).