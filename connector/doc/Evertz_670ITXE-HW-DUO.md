---
uid: Connector_marketing_Evertz_670ITXE-HW-DUO
---

# Evertz 670ITXE-HW-DUO

## About

The Evertz 670ITXE-HW-DUO is a professional broadcast encoder/decoder designed for IP-based media workflows. This DataMiner connector monitors and controls the device over SNMPv2, giving operators real-time visibility into system health, network configuration, signal status, and audio/video processing — all from a single DataMiner element.

## Key Features

- **Comprehensive system monitoring**: Tracks system time, temperature thresholds, product identity, and slot assignment so operators can quickly assess device state without logging into the device web interface.

- **NMOS IS-04/IS-09 integration**: Exposes full NMOS node configuration, including DNS mode (unicast/multicast), device naming, SDP session alias, fallback registry settings, and ST 2110 vs. ST 2022 model selection — enabling seamless participation in software-defined media networks.

- **Reference and timing control**: Allows selection of the timing reference source (PTP, Genlock, or Free-run) and master data port assignment, which is critical for maintaining frame-accurate synchronization in live production environments.

- **IP input quality monitoring**: Provides per-stream monitoring of S2110 IP inputs including RTP error counters for video, audio, and ANC, plus IP input and decoder notification tables (H.264, MPEG-2, HEVC, JPEG, J2K) to detect signal degradation before it reaches air.

- **UDX video and audio processing visibility**: Surfaces UDX video group faults, payload ID faults, PGM video faults, and audio group faults so engineering teams can pinpoint up/down-conversion or audio routing problems at a glance.

- **Breakaway audio IP input management**: Monitors breakaway audio IP input faults, giving operators a dedicated view for independent audio routing issues separate from the main video path.

## Use Cases

### Proactive Fault Detection in Live Broadcast

**Challenge**: In a live broadcast environment, an encoder/decoder fault discovered only when a signal goes to air can cause costly on-air incidents.

**Solution**: DataMiner continuously polls the 670ITXE-HW-DUO's fault and notification tables (decoder notifications, UDX video/audio faults, RTP error counters) and raises alarms the moment thresholds are exceeded or error counts increment.

**Benefit**: Engineering teams receive advance warning of signal degradation, allowing corrective action before the issue impacts the viewer — reducing on-air incidents and mean time to repair.

### Centralized IP Media Network Management

**Challenge**: Managing NMOS node registration, SDP session naming, and ST 2110/ST 2022 mode across dozens of encode/decode devices is error-prone when done device by device through individual web interfaces.

**Solution**: The connector exposes all NMOS and network configuration parameters as read/write DataMiner parameters. Operators can view and update NMOS node enable state, DNS mode, registry addresses, and transport model from a single DataMiner element card or automation script.

**Benefit**: Configuration changes are audited in the DataMiner change log, reducing human error and accelerating commissioning of new IP media infrastructure.

### Reference and Synchronization Assurance

**Challenge**: Timing reference failures (PTP lock loss, genlock dropout) in a multi-device facility are difficult to correlate across systems when each device must be checked individually.

**Solution**: The connector monitors the reference selection state and main data port configuration on the 670ITXE-HW-DUO. When combined with DataMiner correlation rules, a PTP reference change on this device can be correlated with similar events on other elements to identify a facility-wide sync issue.

**Benefit**: Root-cause analysis of timing problems is faster and more reliable, minimizing disruption to live production or playout operations.
