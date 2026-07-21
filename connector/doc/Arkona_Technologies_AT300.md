---
uid: Connector_help_Arkona_Technologies_AT300
---

# Arkona Technologies AT300

## About

The **Arkona Technologies AT300** connector provides centralized monitoring of Arkona AT300 FPGA-based processing cards with a focus on **audio/video delay**, **signal timing alignment**, and **core system metrics**. It gives operators real-time insight into delay configurations, pipeline status, and essential hardware telemetry such as temperature, fans, SFP optical levels, RAM usage, and system uptime.

### Key Features

- **Audio/video delay monitoring**: Track configured delay values, active delay pipelines, and real-time processing status.
- **Signal timing alignment**: Monitor the timing consistency of incoming and outgoing video/audio streams to ensure frame-accurate alignment.
- **System resource telemetry**: View free RAM, FPGA load, CPU usage, and system uptime.
- **Environmental metrics**: Monitor temperature sensors, fan RPM, and thermal thresholds.
- **Optical interface monitoring**: Track SFP RX/TX power levels, link stability, and error counters.

## Use Cases

### Audio and Video Synchronization Assurance

**Challenge**: Lip‑sync issues, timing mismatches, and variable source latency can degrade broadcast quality.

**Solution**: The connector exposes real-time AT300 audio/video delay values and pipeline status.

**Benefit**: Operators can immediately detect misalignments and adjust delays to maintain perfect sync.

### Monitoring Hardware Stability During Live Production

**Challenge**: Environmental issues (temperature, fans, optical signal degradation) can create unexpected outages.

**Solution**: AT300 environmental metrics such as temperature, fans, and SFP power levels are collected and visualized.

**Benefit**: Early detection of hardware issues prevents service interruption.

### Monitoring Performance for Delay Pipelines

**Challenge**: Delay pipelines require predictable processing resources.

**Solution**: The connector provides insight into RAM usage, uptime, and FPGA/system load.

**Benefit**: Ensures delay pipelines run in optimal performance conditions.

## Prerequisites

- AT300 PACs installed in a BLADE runner chassis.
- AT300 management interfaces reachable over the network.
- DataMiner version **10.5.0** or higher.
