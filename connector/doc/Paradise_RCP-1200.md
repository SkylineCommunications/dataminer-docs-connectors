---
uid: Connector_help_Paradise_RCP-1200
---

# Paradise RCP-1200

## About

The **Paradise RCP-1200** connector enables monitoring and control of Paradise amplifiers configured in redundant systems via TCP/IP.

## Key Features

- **Redundancy Monitoring**: Displays the current system redundancy state and amplifier priority setup.
- **Fault Status Monitoring**: Provides real-time visibility of summary faults, power supply faults, and amplifier power faults.
- **System Setup**: Allows configuration overview of system mode, amplifier standby state, and buzzer behavior.
- **RF Switch Position Tracking**: Monitors RF switch position.
- **Communication Information**: Displays protocol and hierarchy configuration.

## Use Cases

### Use Case 1

**Challenge**: Operators need a clear summary of amplifier system health in a redundant configuration.

**Solution**: The connector aggregates fault and status indicators across amplifiers, power supplies, and RF switches.

**Benefit**: Allows quick identification and resolution of system issues, minimizing downtime.

### Use Case 2

**Challenge**: Understanding and validating the communication settings and addressing of each unit in the system.

**Solution**: Displays unit address, baud rate, protocol version, and hierarchy information in one place.

**Benefit**: Simplifies system validation and troubleshooting of communication mismatches.

### Use Case 3

**Challenge**: Managing redundant systems without dedicated automation logic.

**Solution**: Monitors key parameters like standby states, mode (manual/auto), and priority setup.

**Benefit**: Helps engineers verify redundancy configuration and readiness at a glance.

## Technical Reference

### Prerequisites

- **TCP/IP Communication** with access to the device's IP and port.
- **Bus Address** must be known and within 0–31 range.
- **Device Model**: Must be Paradise RCP-1200 series.
- **Minimum Required DataMiner Version**: 10.3.0.0-12752 or higher

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Paradise_RCP-1200_Technical).