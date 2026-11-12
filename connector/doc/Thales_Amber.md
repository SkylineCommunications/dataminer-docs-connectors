---
uid: Connector_help_Thales_Amber
description: "Monitor the Thales Amber DTV remultiplexer over SNMP, including its inputs and outputs, transport streams, services, and PIDs, with trap-driven refresh."
---

# Thales Amber

## About

The **Thales Amber** connector integrates the Thales Amber DTV remultiplexer into DataMiner over SNMP. The Amber is a compact 1RU MPEG-2 remultiplexer that combines up to eight ASI transport streams into a DVB/ATSC-compliant output, with service, PID, and PSI/SI table filtering and re-mapping.

This connector gives headend operators a single view of the unit's **inputs and outputs, transport streams, services, and PIDs**. Besides regular polling, it listens for the alarm appearance and disappearance traps of the device and refreshes the status, service, and PID tables as soon as one is received, so that the element reflects a change in the multiplex within seconds.

## Key Features

- **Monitor transport stream bit rates**: Track the useful, stuffing, and total rate of every stream, with their minimum and maximum values, and the number of services and PIDs carried in each stream. All rates are trended and can be monitored with alarm templates.
- **Supervise services and PIDs**: Follow the running state, bit rate, and name of every service, and the type, scrambling state, and minimum, maximum, and current bit rate of every PID.
- **Check input and output status at a glance**: See all ASI, Ethernet, VSB, QPSK, SDI, CVBS, analog audio, and AES/EBU inputs and all ASI and Ethernet outputs, each with its Not Configured, OK, Warning, or Error state.
- **Navigate the multiplex as a tree**: The Overview page shows the streams, services, and PIDs as a hierarchy, with alarm bubble-up from PID to service to stream.
- **Inventory the unit**: View the unit type, product model, serial number, part number, software versions, redundancy and scrambling capabilities, and the number of inputs, outputs, processors, and HD/SD services the unit supports.
- **Control the polling load**: Switch between fast and slow polling for the whole element, and separately control a fast poll of the input status and TDT configuration.

## Use Cases

### Spotting a Missing or Starved Service Before Viewers Do

**Challenge**: In a multiplex with many services, a service that stops running or a PID whose bit rate collapses is easy to miss until a viewer complains.

**Solution**: The connector alarms on the running state and bit rate of every service and on the bit rate and scrambling state of every PID, and the Overview tree bubbles these alarms up to the service and stream they belong to.

**Benefit**: Operators see which stream, service, and PID is affected in one glance, without browsing the device.

### Reacting Instantly to Device Alarms

**Challenge**: Polling intervals that are gentle on the device mean that a configuration or input change can take a while to show up in the monitoring system.

**Solution**: The connector processes the SNMP traps that the Amber sends when an alarm appears or disappears and immediately refreshes the input and output status, service, and PID tables.

**Benefit**: Combine a low polling load with near-real-time visibility of the multiplex.

## Technical Reference

### Prerequisites

- **SNMP connectivity**: The device must be reachable via SNMP from the DataMiner Agent.
- **Trap destination**: To benefit from the trap-driven refresh, the device must be configured to send its SNMP traps to the DataMiner Agent.
- **Web interface access**: To use the **Embedded Web Server** page, the client machine must have network access to the device.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Thales_Amber_Technical).
