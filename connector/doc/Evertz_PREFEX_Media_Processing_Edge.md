---
uid: Connector_help_Evertz_PREFEX_Media_Processing_Edge
---

# Evertz PREFEX Media Processing Edge

## About

The **Evertz PREFEX Media Processing Edge** connector monitors and controls Evertz PREFEX Media Processing Edge devices via SNMP.
It provides real-time visibility into SMPTE ST 2110-20 (video), ST 2110-30 (audio), and ST 2110-40 (ancillary data)
IP inputs and outputs, allowing operators to track signal presence, stream health, and bitrate, as well as issue
control actions such as clearing error counters and adjusting IP output settings directly from DataMiner.

## Key Features

- **Video (ST 2110-20) IP Input/Output monitoring and control**: Tracks IP input presence, RTP status, signal type,
  and skew, and allows configuration of IP output streams (source IP address, enable/disable, destination settings).
- **Audio (ST 2110-30) IP Input/Output monitoring and control**: Monitors and manages audio-over-IP channels,
  including per-group audio mapping and IP output configuration.
- **ANC (ST 2110-40) IP Input/Output monitoring and control**: Tracks ancillary data IP streams (including
  per-audio-group status) and supports control of ANC IP inputs and outputs.
- **Subtable filtering**: Table polling can be scoped to specific data port/SDI index combinations via a
  configurable subtable filter, reducing SNMP polling overhead on large deployments.
- **Error and statistics management**: RTP sequence error counters and other statistics can be cleared directly
  from DataMiner using dedicated clear buttons.

## Use Cases

### Centralized Monitoring of IP Media Streams

**Challenge**: Broadcast engineers need a single view into the health of SMPTE ST 2110 video, audio, and ancillary
data streams across many Evertz PREFEX Media Processing Edge devices, without having to log into each device
individually.

**Solution**: The connector polls video, audio, and ANC IP input/output tables over SNMP and surfaces signal
presence, RTP status, and error counters directly in DataMiner.

**Benefit**: Operators gain a unified, real-time view of media stream health across the facility, enabling faster
detection and troubleshooting of signal issues.

### Reducing Polling Overhead on Large Systems

**Challenge**: Devices with many data ports and SDI inputs can produce large SNMP tables, increasing polling time
and load on both the device and DataMiner.

**Solution**: The subtable filter parameter lets users scope table polling to only the relevant data
port/SDI index combinations instead of walking the entire table.

**Benefit**: Faster polling cycles and reduced load on the device, while still monitoring the streams that matter.

### Remote Fault Recovery

**Challenge**: RTP sequence errors and other stream statistics can accumulate over time, making it difficult to
identify new issues from historical noise.

**Solution**: Dedicated clear buttons let operators reset error counters and statistics for a given IP input or
output directly from DataMiner, without needing local device access.

**Benefit**: Simplifies fault isolation and recovery, letting engineers quickly re-baseline stream statistics after
resolving an issue.
