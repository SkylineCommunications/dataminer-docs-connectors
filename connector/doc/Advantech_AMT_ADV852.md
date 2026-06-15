---
uid: Connector_Advantech_AMT_ADV852
---

# Advantech AMT ADV852

## About

The Advantech AMT ADV852 is a multi-channel Block Up Converter (BUC) controller used in satellite earth station uplink systems. This DataMiner connector enables centralized monitoring and control of the ADV852 via SNMPv2, providing real-time visibility into BUC operational status, RF power levels, thermal conditions, redundancy configuration, and gain settings — all from within the DataMiner platform.

## Key Features

- **Real-Time BUC Status Monitoring**: Tracks TX status (muted/unmuted), forward power output, TX gain, and attenuation for each BUC module in a continuously updated tabular view.

- **Thermal Monitoring with Alarm Support**: Continuously polls shroud and per-BUC hot spot temperatures with built-in alarm thresholds (warning at 75 °C, critical at 85 °C) to prevent equipment damage.

- **Redundancy Configuration and Control**: Supports 1:1, 1:2 redundant, and phase combiner configurations — including manual and automatic (Auto A/Auto B) redundancy switching for RF paths.

- **Power Supply Supervision**: Monitors dual power supply voltages (PS1 and PS2) to detect supply degradation before it impacts transmission.

- **Remote BUC Control**: Allows operators to mute/unmute RF output, adjust TX gain, switch online/standby states, and reset faults — all remotely via DataMiner.

## Use Cases

### Satellite Uplink Continuity Assurance

**Challenge**: Earth station operators need constant awareness of BUC RF output and forward power levels to prevent signal outages. Manual checks are impractical when managing multiple BUC units across remote sites.

**Solution**: The ADV852 connector polls BUC status every 10 seconds, providing live forward power readings (dBm), TX gain, attenuation, and mute state for each unit. DataMiner trending and alarm monitoring ensure operators are immediately alerted to any deviation.

**Benefit**: Reduced risk of undetected outages, faster response times, and reliable uplink service continuity for satellite broadcast and data services.

### Automated Redundancy Switching Management

**Challenge**: Managing redundant BUC systems (1:1 and 1:2 configurations) manually is error-prone and time-consuming, especially during faults when rapid switchover is critical.

**Solution**: The connector exposes redundancy configuration parameters — including redundancy mode (Manual, Auto A, Auto B), unit position (A/B), and TX switch position — enabling DataMiner Automation scripts to monitor and act on redundancy state changes in real time.

**Benefit**: Faster fault recovery, reduced operator intervention, and improved system availability through automated and auditable redundancy management.

### Proactive Thermal Alarm Management

**Challenge**: BUC units operating at high power levels generate significant heat. Sustained over-temperature conditions can permanently damage RF hardware if not caught early.

**Solution**: The connector continuously monitors both the system-level shroud temperature and per-BUC hot spot temperature, with alarm thresholds pre-configured at warning (75 °C) and critical (85 °C) levels. DataMiner alarm escalation and notifications keep maintenance teams informed before thermal limits are exceeded.

**Benefit**: Extended hardware lifespan, reduced risk of thermal damage, and proactive maintenance scheduling based on real temperature trends.

## Technical Reference

### Prerequisites

- **DataMiner version 10.4.0.0 (build 14003) or higher** is required for this connector to function correctly.

- **SNMPv2 network connectivity** on UDP port 161 is required between the DataMiner Agent and the Advantech AMT ADV852 device.

- **SNMP read/write community strings** are needed for both monitoring and remote control operations (muting, gain adjustment, fault reset, redundancy switching).
