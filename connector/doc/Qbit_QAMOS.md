---
uid: Connector_help_Qbit_QAMOS
---

# Qbit QAMOS

## About

The Qbit QAMOS connector integrates with QAMOS, Qbit's broadcast monitoring system for modern, IP-based workflows. QAMOS offers browser-based control room views with intuitive visualization of audio levels and signal metrics, supports end-to-end monitoring across multiple signal types, and enables multi-input recording of audio and bitstreams for detailed post-event analysis and troubleshooting.

This connector uses the QAMOS REST API to monitor and configure the device from DataMiner.

## Key Features

- **Multi-source input monitoring**: Monitor Icecast, HLS, MPEG-2 TS, EDI, and AES67 inputs side by side from a single element.

- **Stream insights**: Retrieve per-stream metrics such as codec, bitrate, audio buffer fill, channel count, sample rate, and HLS/Icecast specific information.

- **Measurement profile management**: View and configure measurement profiles, including loudness, input loss, silence detection, AES67 invalid SDP, HLS playlist, and EDI superframe sync checks.

- **Alarm management**: List, acknowledge, and review active and past alarms, with controls to limit and clear historical entries.

- **System and network visibility**: Track system info, system health (CPU, memory, up time), and the status and configuration of the device's network interfaces.

## Use Case

**Challenge**: Operations teams need a unified way to monitor audio quality and signal health across heterogeneous IP audio sources, while keeping alarming aligned with the rest of the broadcast facility.

**Solution**: The Qbit QAMOS connector exposes the QAMOS monitoring data inside DataMiner. Inputs, streams, measurement profiles, taps, and alarms are surfaced as DataMiner parameters and tables, so operators can react to issues from the same interface they already use for the rest of their estate.

**Benefit**: Faster fault detection, consistent alarm handling, and a single pane of glass for IP audio monitoring.

## Technical Reference

### Prerequisites

- **Network access**: The Qbit QAMOS device must be reachable over HTTPS from the DataMiner Agent that hosts the element.
- **API credentials**: A valid QAMOS username and password must be available so the connector can obtain a JWT bearer token through the QAMOS authentication endpoint.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Qbit_QAMOS_Technical).
