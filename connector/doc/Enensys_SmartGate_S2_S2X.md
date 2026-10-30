---
uid: Connector_help_Enensys_SmartGate_S2_S2X
description: "Monitor Enensys SmartGate S2/S2X encapsulation gateways, RF modulation, BaseBand Framing, and IP-to-satellite streams in DataMiner."
---

# Enensys SmartGate

## About

The **Enensys SmartGate** connector communicates with the **Enensys SmartGate S2/S2X** (formerly TeamCast) IP-to-satellite encapsulation gateway using SNMP.

Operating as an essential link between IP distribution networks and satellite broadcast infrastructure, the Enensys SmartGate ingests Gigabit Ethernet traffic and encapsulates it into DVB-S2/S2X BaseBand Frames (BBF) using Generic Stream Encapsulation (GSE) or Multi-Protocol Encapsulation (MPE). This connector delivers continuous visibility into RF modulation metrics, input stream health, encapsulation parameters, and network interfaces to maintain uninterrupted satellite transmission.

## Key Features

- **RF transmission and modulation monitoring**: Inspect DVB-S2 and DVB-S2X RF output parameters in real time, including symbol rate, roll-off factor, physical layer scrambling (PLS) code, output frequency, and carrier transmission states.
- **Encapsulation and BaseBand Framing tracking**: Supervise BaseBand Framing (BBF) tables, GSE streams, MPEG-TS stream tables, and detected OpenTMP stream activity across active channels.
- **Multi-port Gigabit Ethernet interface management**: Track link status, throughput, IP configurations, and DHCP lease information across control and data Ethernet interfaces.
- **Input streams and service mapping oversight**: Verify virtual channels, input platform tables, component PID mapping, and service statuses for end-to-end signal tracking.
- **Real-time asynchronous alarm handling**: View changes to power supplies, temperature, and transmission lock in real time thanks to SNMP trap processing.

## Use Cases

### Satellite Broadcast Uplink Monitoring

**Challenge**: Broadcast operators distributing DTH (Direct-To-Home) television or primary contribution feeds over satellite carriers need guaranteed uptime and immediate detection of RF degradation or stream interruptions.

**Solution**: The connector continuously tracks RF modulation parameters, BaseBand Framing, and MPEG-TS stream tables, providing instant visibility into transmission health and carrier lock.

**Benefit**: Engineering teams can detect and resolve signal degradation before broadcast viewers experience transmission blackouts.

### High-Throughput VSAT and IP Encapsulation

**Challenge**: Telecom operators managing VSAT and IP-over-satellite networks face challenges with bandwidth allocation, multi-port interface traffic congestion, and encapsulation stability across diverse IP inputs.

**Solution**: The connector tracks GSE stream rates, VRRP redundancy states, and throughput across control and data Gigabit Ethernet ports to maintain balanced, reliable IP encapsulation.

**Benefit**: Network operations teams optimize transponder utilization and ensure high service availability with rapid failover.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to the [technical documentation page](xref:Connector_help_Enensys_SmartGate_S2_S2X_Technical).
