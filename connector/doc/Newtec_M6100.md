---
uid: Connector_help_Newtec_M6100
---

# Newtec M6100

## About

The **Newtec M6100** is a high-performance satellite modulator used to transmit DVB-S and DVB-S2 (including ACM) carriers for broadcast and data distribution over satellite.

This connector uses SNMP to monitor and control the M6100, giving operators a consolidated view of its modulation settings, input/output interfaces, redundancy status, and alarms directly from DataMiner.

## Key Features

- **DVB-S/DVB-S2 modulation control**: Monitor and configure carrier modulation, symbol rate, roll-off, ModCod, frame type, and output frequency/level of the modulator.

- **Multiple transport stream inputs**: Supports ASI input/output, TS over IP, and TS multiplexing, so you can manage the incoming and outgoing transport stream sources from a single element.

- **Redundancy monitoring**: Tracks the redundancy state of the device, allowing operators to quickly identify failover events and protection status.

- **BISS scrambling management**: Monitor and configure BISS scrambling mode, key parity, and session words to secure transport stream content.

- **Comprehensive alarm reporting**: Surfaces device, interface, and buffer alarms (e.g. frame sync loss, synth failure, buffer under-/overflow) in a unified alarms table for fast troubleshooting.

## Use Cases

### Centralized Modulator Monitoring

**Challenge**: Operators need a quick, reliable way to verify the modulation, output, and streaming parameters of each M6100 in the field without logging into the device's own web interface.

**Solution**: The connector polls the modulator's SNMP MIB to expose modulation mode, symbol rate, output frequency/level, and TS Over IP/ASI interface status directly in DataMiner.

**Benefit**: Reduces the time needed to verify carrier configuration and interface health, enabling faster diagnosis of transmission issues.

### Fast Fault Detection and Redundancy Awareness

**Challenge**: Undetected alarms or an unnoticed redundancy switchover can lead to prolonged service disruptions on critical satellite links.

**Solution**: The connector continuously monitors device, interface, and buffer alarms as well as the redundancy status of the modulator, and reports these directly in DataMiner.

**Benefit**: Enables operators to react immediately to failures or failovers, minimizing downtime on live satellite transmissions.

### Secure Content Delivery

**Challenge**: Broadcasters need to confirm that content scrambling is correctly configured before transmission to prevent unauthorized access to the signal.

**Solution**: The connector exposes BISS scrambling mode, key parity, and session word parameters, allowing operators to verify and manage content protection settings.

**Benefit**: Provides assurance that transmitted content is properly secured, reducing the risk of compliance or content-protection issues.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Newtec_M6100_Technical).
