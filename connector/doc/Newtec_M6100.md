---
uid: Connector_help_Newtec_M6100
---

# Newtec M6100

## About

This connector is used to monitor the M6100 broadcast satellite modulator.

The transport stream analyzer makes it possible to monitor the incoming transport stream. The purpose of this feature is to help determine if a problem seen at the output of a satellite receiver is due to a problem on the satellite link or to a problem in the headend before the modulator. Consequently, it provides the possibility to identify the root cause of service outages that happened in the video headend or on the transmission path between the video MUX and the satellite modulator. Because the analyzer is built into the modulator, inserting it does not change the behavior of the signal or the topology of the network, making troubleshooting easier. This leads to a shorter defect resolution time.

## Key Features

- **DVB-S/DVB-S2 modulation control**: Monitor and configure carrier modulation, symbol rate, roll-off, ModCod, frame type, and output frequency/level of the modulator.

- **Multiple transport stream inputs**: Supports ASI input/output, TS over IP, and TS multiplexing, so you can manage the incoming and outgoing transport stream sources from a single element.

- **Redundancy monitoring**: Tracks the redundancy state of the device, allowing operators to quickly identify failover events and protection status.

- **BISS scrambling management**: Monitor and configure BISS scrambling mode, key parity, and session words to secure transport stream content.

- **Comprehensive alarm reporting**: Surfaces device, interface, and buffer alarms (e.g. frame sync loss, synth failure, buffer under-/overflow) in a unified alarms table for fast troubleshooting.

## Use Cases

### Centralized Modulator Monitoring

**Challenge**: Operators need a quick, reliable way to verify the modulation, output, and streaming parameters of each M6100 in the field without logging into the device's own web interface.

**Solution**: The connector polls the modulator's SNMP MIB to expose modulation mode, symbol rate, output frequency/level, and TS over IP/ASI interface status directly in DataMiner.

**Benefit**: Reduces the time needed to verify carrier configuration and interface health, enabling faster diagnosis of transmission issues.

### Fast Fault Detection and Redundancy Awareness

**Challenge**: Undetected alarms or an unnoticed redundancy switchover can lead to prolonged service disruptions on critical satellite links.

**Solution**: The connector continuously monitors device, interface, and buffer alarms as well as the redundancy status of the modulator, and reports these directly in DataMiner.

**Benefit**: Enables operators to react immediately to failures or failover switches, minimizing downtime on live satellite transmissions.

### Secure Content Delivery

**Challenge**: Broadcasters need to confirm that content scrambling is correctly configured before transmission to prevent unauthorized access to the signal.

**Solution**: The connector exposes BISS scrambling mode, key parity, and session word parameters, allowing operators to verify and manage content protection settings.

**Benefit**: Provides assurance that transmitted content is properly secured, reducing the risk of compliance or content-protection issues.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Newtec_M6100_Technical).
