---
uid: Connector_help_Digidia_SpanFM2
---

# Digidia SpanFM2

## About

The Digidia SpanFM2 connector monitors and controls a Digidia SpanFM2 audio multiplexer. The SpanFM2 is a broadcast headend device that assembles, processes, and synchronizes audio services for DAB/DAB+ and FM radio distribution.

Through an SNMP connection, the connector retrieves the operational status of the multiplexer, surfaces device and multiplex alarms, exposes version and inventory information, and lets operators configure the device network settings, time synchronization, SNMP trap targets, and user access from within DataMiner.

## Key Features

- **Multiplex service monitoring**: Continuous monitoring of the multiplex audio service status, including the audio input, data mailbox input, wave file input, PIMS over RS-232 input, UECP input, synchronization, and redundancy states.

- **Centralized alarm monitoring**: The global alarm table and multiplex alarm notifications are collected and exposed as DataMiner alarms, so that issues on the device are visible in a single overview.

- **Device and network configuration**: Read and set the device network parameters (IP address, subnet mask, gateway, and port speed/duplex) for both Ethernet interfaces, as well as the equipment name, comment, and real-time clock.

- **Time synchronization management**: Monitor the synchronization status and configure the NTP server addresses used by the device.

- **Inventory and version tracking**: Hardware version, software version, MIB version, serial number, and equipment type are collected for asset and lifecycle management.

## Use Cases

### Proactive monitoring of an FM/DAB headend

**Challenge**: Audio input loss, synchronization drift, or a redundancy failure on a broadcast multiplexer can interrupt on-air services if they are not detected quickly.

**Solution**: The connector continuously polls the SpanFM2 multiplex service states and alarm tables and raises DataMiner alarms when any input, synchronization, or redundancy condition becomes active.

**Benefit**: Operators are notified of degradations before they affect listeners, reducing on-air downtime.

### Centralized configuration of distributed devices

**Challenge**: Broadcast networks often contain many multiplexers spread across remote sites, making manual per-device configuration time-consuming.

**Solution**: Network settings, NTP servers, SNMP trap targets, and user accounts can be reviewed and updated directly from the DataMiner element.

**Benefit**: Consistent configuration across the fleet from a single pane of glass, without needing direct access to each device web interface.

### Inventory and lifecycle reporting

**Challenge**: Keeping an accurate overview of firmware and hardware versions across a deployment is difficult when relying on manual records.

**Solution**: The connector reports the software, hardware, and MIB versions together with the serial number and equipment type for every monitored device.

**Benefit**: Up-to-date inventory data supports maintenance planning, firmware roll-outs, and compliance reporting.

## Technical Reference

### Prerequisites

- **DataMiner 10.4.0.0 (build 14003) or higher** is required to host the connector.
- **SNMP** must be enabled and reachable on the Digidia SpanFM2 device for monitoring and control.
- The correct **Get** and **Set** community strings are needed to read values and to apply configuration changes.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Digidia_SpanFM2_Technical).
