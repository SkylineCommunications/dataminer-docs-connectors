---
uid: Connector_help_CISCO_Nexus
description: Monitor Cisco Nexus switches in DataMiner using SNMP, SSH, NX API, gNMI, APIC API polling, automation, and DCF integration.
---

# CISCO Nexus

## About

The Cisco Nexus switches are modular and fixed-port network switches designed for data centers. With this connector, you can monitor and control these switches in DataMiner.

The connector uses an **SNMP** main connection and can also communicate with the device via **SSH**, **NX API** (HTTPS), and **gNMI**. For NBM flow statistics, the connector can send **APIC API** requests over HTTPS to the element's polling IP.

## Key Features

- **In-depth interface monitoring**: Detailed interface information with Rx/Tx statistics, bit rates and utilization, L2/L3 configuration, MAC addresses, switch port information, and SFP transceiver details.

- **System health and environment**: Monitoring of sensors, fans, power supply units, CPU, and memory.

- **Timing and synchronization**: PTP clock, grandmaster, interface, and correction information, as well as NTP monitoring.

- **Routing and redundancy**: BGP peers, OSPF, HSRP groups, port channels, and virtual port channels.

- **IP media network support**: NBM interface bandwidth and flow statistics, RTP flows, IGMP, and QoS.

- **Layer 2 management**: VLAN/VTP configuration and monitoring, STP, CDP, LLDP, and PoE.

- **Interactive CLI**: Commands can be sent to the switch via SSH or NX API directly from DataMiner, with a persistent command history.

- **Streaming telemetry**: gNMI (OpenConfig) data collection for interface statistics.

- **Automation integration**: From version **3.0.9.1 onwards**, DataMiner Automation scripts can send one or more CLI commands to the connector using an InterApp call. The connector executes the commands through NX API and returns a result for each command. For more information, see [Sending NX API Commands from Automation Scripts](xref:Connector_help_CISCO_Nexus_Technical#sending-nx-api-commands-from-automation-scripts).

- **DCF support**: Ethernet interfaces and VLANs are automatically available as DCF interfaces.

## Use Cases

### Data Center Fabric Monitoring

**Challenge**: Data center operators need continuous visibility into the health and performance of their switching fabric, across many devices and thousands of interfaces.

**Solution**: The connector polls interface statistics, system health, sensors, and routing protocol state via SNMP, enriched with NX API and gNMI data where available.

**Benefit**: A single element per switch provides complete fabric visibility, with alarming and trending on all key metrics.

### IP Media Network Operations

**Challenge**: In ST 2110 and other IP media networks, operators must track NBM flow bandwidth, IGMP state, and PTP synchronization to guarantee uninterrupted media transport.

**Solution**: The connector can retrieve NBM flow statistics through the APIC API, monitors IGMP and PTP state, and exposes RTP flow information.

**Benefit**: Media-critical network behavior is monitored in the same platform as the rest of the media chain, enabling fast root-cause analysis.

### Remote Switch Management

**Challenge**: Engineers need to execute show and configuration commands on switches without opening a separate terminal session for each device.

**Solution**: The interactive CLI page allows commands to be sent via SSH or NX API directly from DataMiner, with command history and communication status feedback.

**Benefit**: Centralized, audited access to switch CLI operations from within DataMiner.

## Technical Reference

### Prerequisites

- **DataMiner 10.4.0.0 (build 14003) or higher** is required for the main connector range.
- **Credentials** with the necessary privileges are required for SSH, NX API, gNMI, APIC API, and interactive CLI functionality.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_CISCO_Nexus_Technical).
