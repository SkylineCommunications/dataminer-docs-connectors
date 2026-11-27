---
uid: Connector_help_SYes_SILM5-03_DAB_TX-PCM_VHF_Transmitter
description: Monitor and control the SYes SILM5-03 DAB VHF transmitter over SNMPv3 - RF power, exciters, amplifiers, inputs, switching, and alarms.
---

# SYes SILM5-03 DAB TX-PCM VHF Transmitter

## About

The **SYes SILM5-03** is a VHF transmitter for Digital Audio Broadcasting (DAB). This connector communicates with the transmitter via **SNMPv3** and provides centralized monitoring of RF power output, exciter and amplifier health, input signal status, and transmitter alarm states, as well as remote control of exciter and input switching behavior.

## Key Features

- **Real-time RF power monitoring**: Track antenna and dummy-load forward and reflected power in mW, dBm, and percentage of nominal power, with an automatically calculated power derating value to detect performance degradation at a glance.

- **Dual exciter oversight**: Monitor both exciters simultaneously, including status, output power, temperature, fan health, time reference source, and firmware bank state, so redundancy readiness is visible at all times.

- **Amplifier module monitoring**: Follow working state, RF status, forward power, total current, temperature, and PSU, fan, reflected-power, and temperature conditions for each amplifier module.

- **Exciter switching and input management control**: Configure switch mode, switch policy, delay timers, and the preferential exciter, set the input management switch mode and maximum PPS difference, and monitor input selection, hitless switching, and reference lock status.

- **Power threshold visibility**: Track the transmitter's low-power and reflected-power warning and alarm thresholds alongside live output, together with transmission mode and channel frequency.

## Use Cases

### Unattended Remote Transmitter Site Monitoring

**Challenge**: DAB transmitter sites are often located at remote hilltop or tower locations with no permanent staff, making it difficult to detect RF performance issues or equipment faults before they affect broadcast coverage.

**Solution**: The connector continuously polls power metrics, exciter and amplifier status, and PSU, interlock, and lockout states, surfacing conditions such as low forward power or excessive reflected power as soon as they occur.

**Benefit**: Operations teams gain 24/7 visibility from a central NOC, enabling faster fault response, fewer truck rolls, and improved transmitter uptime.

### Exciter Redundancy Assurance

**Challenge**: Maintaining seamless failover between dual exciters requires continuous awareness of each exciter's health and correct configuration of the switchover policy, which is hard to verify through periodic site visits alone.

**Solution**: The connector shows per-exciter health and spare exciter availability in a single table and provides control over switch mode, policy, delay timers, and the preferential exciter.

**Benefit**: Broadcast engineers can verify redundancy readiness at a glance and fine-tune switchover behavior remotely, reducing the risk of dead-air events caused by undetected exciter degradation.

### Input Signal Integrity

**Challenge**: A DAB transmitter depends on a valid input stream and a stable time reference; loss of the external reference, 10 MHz lock, or an input interface fault leads to degraded or interrupted transmission.

**Solution**: The connector monitors input physical interface status, the input module, external and 10 MHz reference state, PPS difference, and the input on air, and allows the **Input Management Switch Mode** and maximum PPS difference to be configured.

**Benefit**: Input problems are detected and corrected before they propagate to the RF output.

## Technical Reference

### Prerequisites

- **SNMPv3 network access** is required between the DataMiner Agent and the SYes SILM5-03 transmitter (default port *161*).

- **DataMiner version 10.4.0.0 - 14003** or higher is required.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_SYes_SILM5-03_DAB_TX-PCM_VHF_Transmitter_Technical).
