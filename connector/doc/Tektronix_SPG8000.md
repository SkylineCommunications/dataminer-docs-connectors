---
uid: Connector_help_Tektronix_SPG8000
---

# Tektronix SPG8000

## About

The **Tektronix SPG8000** connector monitors and manages Tektronix SPG8000 master clock systems in DataMiner. It combines SNMP monitoring with the device's API to provide visibility into timing references, synchronization status, signal outputs, hardware health, and alarms.

## Key Features

- **Master clock health monitoring**: Monitor overall device status, uptime, firmware information, temperature, battery status, and front-panel LED states.

- **Reference and synchronization visibility**: Monitor GPS, genlock, time status, signal quality, satellites, and loss-of-lock conditions.

- **PTP monitoring**: Track Precision Time Protocol status, including clock identity, domain, priorities, clock class, clock accuracy, steps removed, and time offset information.

- **Signal and output monitoring**: Monitor LTC, black, SDI, AES, embedded audio, and Dolby E interfaces, including video, ancillary data, timecode, and metadata information.

- **Hardware and alarm supervision**: Monitor board voltages, fan speeds, power supply status and test history, as well as device alarms received through traps.

## Use Cases

### Broadcast timing infrastructure monitoring

**Challenge**: Timing and synchronization issues can affect multiple downstream broadcast systems, while device status may otherwise require separate access to each master clock.

**Solution**: Use the connector to centralize SPG8000 status, reference information, synchronization indicators, and alarm conditions in DataMiner.

**Benefit**: Operators can identify timing problems earlier and correlate them with other monitored broadcast infrastructure.

### PTP grandmaster supervision

**Challenge**: PTP deployments require visibility into the active clock state and synchronization quality across the timing network.

**Solution**: Use the PTP status data to monitor clock identity, domain, priorities, clock quality, steps removed, and offset-related information.

**Benefit**: Network operators gain the information needed to verify grandmaster operation and investigate synchronization changes.

### Signal-path and hardware health checks

**Challenge**: Faulty fans, power supplies, voltages, or output interfaces can compromise timing and reference distribution.

**Solution**: Monitor hardware health, power supply test history, voltage levels, fan speeds, reference inputs, and SDI/audio-related status from the DataMiner element.

**Benefit**: Maintenance teams can detect developing hardware issues and troubleshoot signal or reference failures from a single operational view.


### Exported connector

The connector exports a **Tektronix SPG8000 - PTP Interface** child connector for PTP-related monitoring. Connectivity for the exported connector is managed by the parent connector.
