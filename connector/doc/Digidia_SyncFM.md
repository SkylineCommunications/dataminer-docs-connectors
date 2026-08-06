---
uid: Connector_help_Digidia_SyncFM
description: Monitor and control Digidia SyncFM devices in DataMiner, including SyncFM2 and SyncFM4, with GPS sync visibility and SNMP alarms.
---

# Digidia SyncFM

## About

The Digidia SyncFM connector monitors and controls Digidia SyncFM devices, including SyncFM2 and SyncFM4 audio processors, used to synchronize FM radio networks. In a Single Frequency Network (SFN), multiple transmitters share the same frequency, so the audio they emit must be time-aligned to avoid interference in overlap zones. SyncFM devices use a GPS time reference to lock audio and RDS/user-channel data distributed over IP to each transmitter site, helping you maintain sample-accurate synchronization across the network.

Through SNMP polling and SNMP trap handling, this connector surfaces the full operational state of the device in DataMiner: GPS reception quality, synchronization mode and status, IP audio input health, user-channel data distribution, and hardware, software, and process alarms.

## Key Features

- **GPS synchronization monitoring**: Real-time visibility of GPS lock status, number of visible satellites, average satellite SNR, leap seconds, cable delay, and decoded receiver position.

- **SFN/MFN synchronization control**: Read and set the synchronization operating mode (Single Frequency Network or Multi Frequency Network) and monitor auxiliary output clock frequency and system clock lock state.

- **IP audio input supervision**: Configure and monitor IP input connection mode, multicast group address, and port, with dedicated alarms for input underflow, overflow, and uncorrected packets.

- **User-channel and audio distribution management**: Track user-channel database version, active group, program identifiers (SCID), studio number, transmitter time delay, and breaking-program settings used to distribute audio to transmitter sites.

- **Comprehensive alarm monitoring with SNMP traps**: Aggregated alarm status for synchronization, IP input, control process, and system, plus granular alarms (SFN error, GPS receiver unlocked, hardware/software faults, empty user-channel database, and more) updated by polling and device-generated traps.

## Use Cases

### Guaranteeing On-Air Synchronization of an FM SFN

**Challenge**: In a Single Frequency Network, all transmitters broadcast on the same frequency. Any drift in the GPS reference or distributed audio timing can create audible interference in overlap zones, and these issues are hard to detect from a central location.

**Solution**: The connector continuously polls GPS lock status, satellite count, SNR, synchronization mode, and the SFN error alarm, and raises alarms as soon as the reference or synchronization degrades.

**Benefit**: You are alerted to synchronization problems before they affect listeners, and you can quickly determine whether the root cause is GPS reception, IP input, or the device itself.

### Centralized Health Monitoring of Distributed Transmitter Sites

**Challenge**: SyncFM devices are typically deployed across many remote transmitter sites, each with its own GPS antenna, IP feed, and hardware, making manual supervision impractical.

**Solution**: DataMiner aggregates alarm status for each device (IP input, synchronization, control process, and system) and enriches it with notifications sent through SNMP traps.

**Benefit**: You can view the entire network from a single pane of glass and detect and localize faults at unmanned sites faster.

### Verifying and Adjusting Audio Distribution Configuration

**Challenge**: Correct on-air behavior depends on user-channel configuration, program identifiers, and transmitter time delays being set consistently across the network.

**Solution**: The connector exposes user-channel parameters (database version, active group, program SCID and mode, transmitter time delay, IP input settings, and auxiliary clock frequency) as monitored and, where supported, settable values.

**Benefit**: You can audit and correct distribution configuration remotely from DataMiner, helping maintain consistent settings across all transmitter sites.

## Technical Reference

### Prerequisites

- **SNMP access to the device** is required so DataMiner can poll status and configuration parameters. SNMP must be enabled on the SyncFM device with the correct read/write community strings, and the polling port (default 161) must be reachable.

- **SNMP trap configuration on the device** is required for real-time alarm notifications. The SyncFM device must be configured (via the Trap page / SNMP Trap Settings) to send traps to the DataMiner Agent so the connector can process alarm events as they occur.

- **A valid GPS reference** is required on the device side for synchronization to function. The connector reports GPS reception quality but depends on a correctly installed GPS antenna at the transmitter site.

- **Network connectivity** between the DataMiner Agent and the device is required for SNMP polling and, optionally, access to the device web interface.

> [!NOTE]
> For detailed technical information, refer to [technical documentation](xref:Connector_help_Digidia_SyncFM_Technical).
