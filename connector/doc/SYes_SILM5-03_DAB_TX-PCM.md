---
uid: Connector_help_SYes_SILM5-03_DAB_TX-PCM
---

# SYes SILM5-03 DAB TX-PCM VHF Transmitter

## About

The **SYes SILM5-03** is a VHF DAB transmitter designed for digital audio broadcasting. This DataMiner connector communicates with the transmitter via **SNMPv2**, enabling centralized monitoring of RF power output, exciter health, input redundancy, and alarm states — giving broadcast engineers full operational control from a single pane of glass.

## Key Features

- **Real-time RF power monitoring**: Track antenna forward and reflected power in kW, dBm, and percentage, with automatic power derating calculation to detect performance degradation at a glance.

- **Dual exciter oversight**: Monitor both exciters simultaneously — including output power, temperature, connection status, fan health, and firmware integrity — ensuring redundancy readiness at all times.

- **Automatic input switching with hitless support**: Configure manual or automatic input switching policies with adjustable delay timers and preferred-input selection, minimizing on-air interruptions during source failover switches.

- **Centralized alarm management**: Surface critical transmitter alarms — PSU faults, interlock failures, lockout states, low-power warnings, and reflected-power threshold breaches — directly within DataMiner for immediate operator awareness.

- **Remote threshold configuration**: Adjust low-power and reflected-power warning/alarm thresholds, transmission mode, channel frequency, and exciter reference sources remotely without on-site visits.

## Use Cases

### Unattended Remote Transmitter Site Monitoring

**Challenge**: DAB transmitter sites are often located at remote hilltop or tower locations with no permanent staff, making it difficult to detect RF performance issues or equipment faults before they impact broadcast coverage.

**Solution**: The connector polls power metrics every 10 seconds and alarm states every 30 seconds, immediately surfacing conditions such as low forward power, excessive reflected power, PSU failures, or interlock alarms within the DataMiner Alarm Console.

**Benefit**: Operations teams gain 24/7 visibility from a central NOC, enabling faster fault responses, reduced truck rolls, and improved transmitter uptime.

### Exciter Redundancy Assurance

**Challenge**: Maintaining seamless failover between dual exciters requires continuous awareness of each exciter's health and correct configuration of switchover policies — something that is hard to verify from periodic site visits alone.

**Solution**: The connector monitors both exciters in a detailed table view — tracking status, temperature, output power, fan health, and firmware consistency — while providing control over switch mode, policy, delay timers, and preferred exciter settings.

**Benefit**: Broadcast engineers can verify redundancy readiness at a glance and fine-tune switchover behavior remotely, significantly reducing the risk of dead-air events caused by undetected exciter degradation.

### Multi-Transmitter Network Oversight

**Challenge**: Broadcast networks operating many SYes SILM5-03 transmitters across different regions need a unified way to compare performance, standardize alarm thresholds, and correlate events across the entire fleet.

**Solution**: Each transmitter instance integrates into DataMiner with consistent parameter naming, alarm templates, and trending, enabling aggregated dashboard views that consolidate power output, derating, input status, and alarm summaries across all sites.

**Benefit**: Network planners achieve a single operational view of their entire DAB transmission infrastructure, streamlining SLA reporting, capacity planning, and coordinated maintenance scheduling.

## Technical Reference

### Prerequisites

- **SNMPv2 network access** is required between the DataMiner Agent and the SYes SILM5-03 transmitter (default port: 161).

- **DataMiner version 10.3.0.0 - 12752 or higher** is required for this connector.

### Polling Configuration

The connector uses three polling timers to balance responsiveness with network efficiency:

| Timer | Interval | Data |
|--|--|--|
| Fast | 10 seconds | System uptime, antenna, and load forward/reflected power (mW, dBm, %) |
| Medium | 30 seconds | Exciter table, input status, switch configuration, PSU and switch alarms, transmitter warnings |
| Slow | 1 hour | System identification, nominal power, power thresholds, amplifier information |
