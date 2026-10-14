---
uid: Connector_help_TestTree_StreamProbe
description: "Learn how the TestTree StreamProbe connector helps investigate broadcast delivery issues using stream, program, PID, RF, OTT, and provisioning data."
---

# TestTree StreamProbe

## About

The **TestTree StreamProbe** connector brings broadcast and streaming probe data into DataMiner. It helps operators investigate delivery issues by linking transport streams to programs, PIDs, quality measurements, and alarms, alongside RF, OTT, and provisioning information.

## Key Features

- **Probe and content monitoring**: Monitor availability, CPU and memory usage, bitrate, and declared versus active content to identify probe health and content availability issues.
- **Transport stream analysis**: Use program and PID status, ETR measurements, and audio and video quality indicators to locate errors within MPEG transport streams.
- **RF and OTT diagnostics**: Compare RF receiver status with tuning configuration and inspect OTT service diagnostics to investigate reception and streaming issues.
- **Provisioning visibility**: Inspect ABR provisioning and configured SMPTE ST 2110 services and their streams on blue and red networks to verify the monitored configuration.
- **Content membership**: Use configured group and macro service memberships to identify related monitored content and focus investigations.
- **Polling and connectivity controls**: Control dataset polling intervals to adjust collection frequency and expose connectivity through the DataMiner Connectivity Framework (DCF).

## Use Cases

### Broadcast Fault Investigation

**Challenge**: A broadcast delivery fault needs to be traced to the affected transport stream, program, or PID.

**Solution**: Follow the transport stream through its programs and PIDs, examining ETR measurements and audio and video quality indicators alongside probe alarms.

**Benefit**: Operators can identify affected content and relate measured errors to reported alarms.

### RF and OTT Diagnostics

**Challenge**: Content is unavailable or degraded at an RF receiver or OTT service.

**Solution**: Compare RF tuning configuration with receiver status and measurements, or inspect diagnostics for the affected OTT service.

**Benefit**: Operators can assess reception conditions or service diagnostics before deciding what to investigate next.

### ST 2110 Provisioning Verification

**Challenge**: A configured SMPTE ST 2110 service needs to be checked against its monitored media streams.

**Solution**: Inspect the service configuration and compare its constituent streams on the blue and red networks with monitoring data.

**Benefit**: Operators can verify the configured service and network assignments without changing the configuration.

### Scoped Content Investigation

**Challenge**: An issue affects related content within a larger set of monitored streams.

**Solution**: Select the relevant probe and use configured group or macro service membership to identify related content.

**Benefit**: Operators can focus their investigation on the relevant members instead of reviewing every monitored stream.

## Technical Reference

### Prerequisites

- DataMiner **10.3.0.0-12752** or higher.
- A TestTree StreamProbe with an HTTP API reachable from the DataMiner Agent.
- SNMP trap connectivity from the probe to the DataMiner Agent.

### Supported Firmware

Documented firmware support is **5.0.6i-a**. Support for other firmware versions is not established by the existing documentation.

> [!NOTE]
> See the [technical documentation](xref:Connector_help_TestTree_StreamProbe_Technical) for connection settings, monitoring and provisioning workflows, polling controls, and cleanup limitations.
