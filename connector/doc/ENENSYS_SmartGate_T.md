---
uid: Connector_help_ENENSYS_SmartGate_T
description: Monitor ENENSYS SmartGate T DVB-T/DTMB SFN adapters in DataMiner, with visibility into alarms, logs, GPS, device health, and IP statistics.
---

# ENENSYS SmartGate T

## About

The ENENSYS SmartGate T connector brings DVB-T/DTMB SFN adapter status and operational data into DataMiner. It provides visibility into device health, timing, alarms, event logs, and IP transport statistics, with selected device controls available from the element.

## Key Features

- **Alarm and event visibility**: Review device status, active alarms, alarm configuration, and event logs.
- **Broadcast timing and health**: Monitor temperature, reference clock, GPS quality, satellite counts, firmware, and device information.
- **IP transport insight**: View bitrate, jitter, packet counters, and forward error correction (FEC) statistics.
- **Operational controls**: Reboot or identify the device, clear its logs, and manage trap destinations, including replaying active alarms.
- **Flexible polling**: Adjust polling intervals, enable or disable individual datasets, and request on-demand polls.

## Use Cases

### Monitor broadcast equipment health

**Challenge**: A transmission path can be affected by device health or timing issues that are difficult to spot across equipment.

**Solution**: Bring temperature, reference clock, GPS status, alarms, and device status into DataMiner.

**Benefit**: Operators can review relevant health and timing indicators alongside other monitored infrastructure.

### Investigate IP transport issues

**Challenge**: Packet loss, jitter, or insufficient bitrate can affect the quality of an IP stream.

**Solution**: Use the connector's IP statistics for bitrate, jitter, packet counters, and FEC information.

**Benefit**: Operators can use device-reported transport statistics to support troubleshooting.

### Review alarms and device events

**Challenge**: Active alarms and historical events may need to be reviewed or delivered to monitoring destinations.

**Solution**: Inspect current alarms and logs, configure trap destinations, and replay active alarms when needed.

**Benefit**: Alarm and event information is available from the DataMiner element, with controls for follow-up actions.

## Technical Reference

### Prerequisites

- DataMiner 10.4.0.0 build 14003 or later.
- SNMPv2c connectivity to the device. The default SNMP port is UDP 161.
- An SNMP read community is required for monitoring. An SNMP write community is required for configuration changes and device controls.

### Monitored information and controls

The connector provides pages for general device information, system and GPS status, alarms and logs, IP statistics, IP configuration, and polling. Network and IP configuration data are read-only. Available controls include rebooting the device, clearing logs, and managing trap destinations.

The Polling page lets operators configure each dataset's interval and enabled state, or poll an enabled dataset on demand. Polling intervals and enabled states are retained across element restarts.

### Security and compatibility

SNMPv2c traffic is not encrypted. Use network controls appropriate to your deployment. Firmware compatibility has not been verified; the repository does not specify a supported firmware range.