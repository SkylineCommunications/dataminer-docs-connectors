---
uid: Connector_help_GatesAir_Maxiva_VAX_Transmitter
---

# GatesAir Maxiva VAX Transmitter

## About

The GatesAir Maxiva VAX is a high-power UHF/VHF television transmitter platform. This connector monitors and controls the central unit of the Maxiva VAX, providing real-time visibility into transmitter health, RF performance, external amplifier status, and liquid cooling system state.

## Key Features

- **RF Power Monitoring**: Tracks forward and reflected power (W and dBm) for the transmitter and each external amplifier modules in real time.

- **External Amplifier Overview**: Polls info, status, PSU, and alarm tables for T3 and T1/T2 amplifier topologies, covering current, PSU presence, fan, and interlock alarms per cabinet and module index.

- **Liquid Cooling System Monitoring**: Provides full visibility into liquid controller status, PSU health, blower state, fuse status, flow, pressure, and temperature — including dangerous-level alarms.

- **Trap-Driven Event Log**: Processes incoming SNMP traps in real time and stores them in a event log table, retaining the most recent events with timestamp, priority, and alarm description.

## Use Cases

### Use Case 1

**Challenge**: A facility runs multiple external amplifier cabinets per transmitter and needs to pinpoint which specific module or PSU has failed without sending a technician on-site.

**Solution**: The connector polls per-cabinet, per-module alarm tables (External Amplifier Alarm, T3 PSU, T1/T2 PSU) and surfaces individual alarm columns with DataMiner alarm monitoring and trending enabled.

**Benefit**: Maintenance teams can identify the exact failing component remotely, reducing mean time to repair and avoiding unnecessary site visits.

## Technical Reference

### Prerequisites

- **SNMP trap forwarding** must be configured on the device to point to the DataMiner Agent IP address so that event log and alarm updates are received in real time.
