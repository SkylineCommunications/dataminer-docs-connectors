---
uid: Connector_help_Evertz_Xenon_Switch
---

# Evertz Xenon Switch

## About

The **Evertz Xenon Switch** connector monitors and controls the Evertz Xenon series routing switcher. It provides real-time visibility into the state of the routing matrix, installed cards, and active faults, while enabling full crosspoint control directly from DataMiner. The connector communicates over SNMP for status and fault data, and over the Evertz Q-Link serial protocol for matrix routing control, with optional redundant controller support.

## Key Features

- **Up to 128×128 matrix control**: View and set crosspoints through a native DataMiner matrix UI, with per-level routing and manual refresh options.

- **Redundant controller management**: Monitors which controller (main or redundant) is currently active and allows seamless switching between them directly from the element.

- **Card and reference card status**: Tracks the operational state of all installed cards and reference cards in a dedicated table, enabling proactive hardware health monitoring.

- **Fault monitoring with SNMP trap support**: Displays active faults from the device in a structured table, including individual fault status and trap-sending configuration, ensuring alarm visibility in DataMiner.

- **DCF integration**: Exposes all inputs and outputs as DataMiner Connectivity Framework (DCF) interfaces, enabling end-to-end signal path tracing across the DataMiner topology.

## Use Cases

### Centralised Routing Control in a Broadcast Facility

**Challenge**: Operators need to manage signal routing on an Evertz Xenon switcher from a unified control interface, without relying on vendor-specific tools.

**Solution**: The connector exposes the full routing matrix in the DataMiner Matrix UI, allowing operators to set crosspoints, lock destinations, rename inputs and outputs, and browse matrix levels — all from within DataMiner.

**Benefit**: Reduces the need for separate vendor tools, speeds up routing operations, and enables routing changes to be automated through DataMiner Automation scripts.

### Proactive Hardware Fault Detection

**Challenge**: Card failures or reference signal issues on the Xenon chassis may go unnoticed until they impact on-air signals.

**Solution**: The connector continuously polls card status and fault tables via SNMP and raises DataMiner alarms when a card enters a fault state or a monitored fault becomes active.

**Benefit**: Operations teams receive immediate alarm notifications in DataMiner, enabling faster incident response and reducing unplanned downtime.

### End-to-End Signal Path Verification

**Challenge**: In complex signal chains, it is difficult to trace which source is routed to which destination and verify connectivity across multiple devices.

**Solution**: The connector registers all inputs and outputs as DCF interfaces, and the current crosspoint state is reflected as DCF connections. DataMiner can then combine this with DCF data from other elements to build a complete signal path map.

**Benefit**: Engineers can visually verify end-to-end connectivity in DataMiner Visual Overview diagrams, simplifying fault isolation and infrastructure audits.

## Technical Reference

### Prerequisites

- **SNMP access** is required for card status, fault monitoring, and general device information polling.

- **Network reachability to the Q-Link serial port** is required to enable matrix routing control (crosspoint get/set, label read/write, lock/unlock). This can be disabled if only SNMP monitoring is needed.

- **A secondary IP address** for the redundant controller is required if redundant controller failover monitoring and switching are needed.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_technical_Evertz_Xenon_Switch).