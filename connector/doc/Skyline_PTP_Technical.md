---
uid: Connector_help_Skyline_PTP_Technical
description: Technical reference for Skyline PTP, covering in-connector mediation architecture, data pages, mediated tables, and supported PTP connectors.
---

# Skyline PTP Technical

This page describes the technical architecture, data pages, and mediated tables for version 2.0.0.X of the **Skyline PTP** connector. It also serves as the single definitive source of truth for supported vendor connectors.

## Technical Architecture

Starting with range 2.0.0.X, the Skyline PTP connector introduces an **in-connector mediation** architecture that replaces the legacy Standard DataMiner PTP Device mediation protocol.

Instead of relying on an external mediation protocol, the Skyline PTP connector communicates directly with remote vendor elements. It subscribes to parameter changes on monitored vendor devices, providing real-time data ingestion, reduced processing overhead, and higher scalability across complex PTP networks.

## Data Pages

The Skyline PTP connector includes several data pages and tables that ingest, process, and organize PTP topology and device metrics:

### Supported PTP Protocols

**Table 7000 (Supported PTP Protocols)** defines all vendor protocols supported by the in-connector mediation engine, including their parameter mappings, supported clock types, and configuration rules. This table serves as the internal protocol registry used by the connector to handle incoming element data.

### Mediated Parameters

**Table 3000 (Mediated Parameters)** contains real-time PTP parameters collected per device:

- Clock identity and domain number
- PTP clock class, accuracy, and priority settings (Priority 1 and Priority 2)
- Offset from master and mean path delay
- Parent dataset information (parent clock identity, grandmaster identity, and grandmaster clock quality)
- Device communication and synchronization status

### Mediated Ports

**Table 3200 (Mediated Ports)** contains port-level PTP operational status and performance metrics for all monitored devices:

- Port identity and port number
- Port state (such as *Master*, *Follower*, *Passive*, *Listening*, or *Disabled*)
- Log message intervals (announce, sync, and delay request intervals)
- Peer mean path delay and delay mechanism

### Mediated Foreign Masters

**Table 3400 (Mediated Foreign Masters)** tracks foreign master records received by PTP ports on boundary clocks and follower devices:

- Foreign master clock identity
- Foreign master port number
- Number of announce messages received from the foreign master

### Mediated Transparent Clock Ports

**Table 3600 (Mediated Transparent Clock Ports)** contains operational parameters specific to transparent clock ports:

- Port identity and port state
- Log minimum delay request interval
- Peer mean path delay

## Supported PTP Connectors

This section is the **single definitive source of truth** for all vendor connectors supported by the [DataMiner PTP Solution](https://aka.dataminer.services/PTPHelp) and the Skyline PTP in-connector mediation engine.

The following table lists all supported vendor connectors:

| Connector |
|----------------------|
| ADVA Optical Networking OSA 5422 |
| Arista Manager |
| Arista eOS Manager |
| Bridge Technologies VB Probe Series |
| CISCO Nexus |
| directOut montone.42 |
| Evertz 5700MSC |
| Evertz 5700MSC - PTP Interface |
| Evertz DreamCatcher |
| Generic Edge Chassis |
| Generic Edge Chassis - PTP Card |
| Generic Switch |
| Hirschmann - a Belden Brand MAR 1040 |
| Imagine Communications Selenio Network Processor |
| Juniper Networks Manager |
| Lawo HD Core Ravenna |
| Lawo Power Core |
| Lawo V__matrix |
| Meinberg LANTIME IMS-HPS - PTPv2 Instance |
| Meinberg LANTIME IMS-HPS API V10 - PTPv2 Instance |
| Meinberg LANTIME IMS-PSX API V17 - PTPv2 Instance |
| Meinberg Lantime M3000 - PTPv2 Module |
| Mellanox Technologies MLNX-OS Manager |
| Pebble Beach Dolphin |
| Riedel Communications MediorNet MuoN (FusioN and VirtU) |
| Ross Video Iggy-AES16.16 |
| Ross Video Newt-IPR-3G-4S |
| Seiko Time Server Pro. TS-1550 |
| Seiko Time Server Pro. TS-2950 |
| Tektronix Prism |
| Tektronix SPG8000 - PTP Interface |
