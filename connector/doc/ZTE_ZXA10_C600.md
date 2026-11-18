---
uid: Connector_help_ZTE_ZXA10_C600
description: "Learn how to configure and use the ZTE ZXA10 C600 connector to monitor OLT chassis health, optical links, and subscriber interfaces."
---

# ZTE ZXA10 C600

## About

The ZTE ZXA10 C600 connector monitors the ZTE ZXA10 C600 GPON OLT chassis via SNMPv2. It provides visibility into chassis health, board and power status, uplink optical (SFP) status, and the GPON/XGS-PON and Ethernet interfaces that deliver subscriber services, and all this from within DataMiner, without relying on the vendor's own element management system.

## Key Features

- **Chassis and board health monitoring**: Catch any hardware issues early thanks to tracking of board temperature, board power, power module, and CPU/system status.

- **Uplink optical monitoring**: Spot optical degradation before it causes an outage, thanks to tracking of Rx/Tx optical power on uplink SFPs, with configurable SFP power thresholds.

- **GPON and XGS-PON service visibility**: Gain insight into subscriber-facing service health, with visibility into GPON interfaces, GPON channels, XGS-PON channels, and PON interface status.

- **Ethernet interface monitoring**: View standard and vendor-specific Ethernet interface status, rates, and bandwidth utilization.

- **LLDP neighbor discovery**: Gain topology awareness with local port and remote-neighbor LLDP tables.

- **Configurable polling**: Tune the load on large deployments by enabling or disabling individual polling groups.

## Use Cases

### Proactive Optical-Link Degradation Detection

**Challenge**: Optical uplinks degrade gradually, and by the time a customer notices, service has already been impacted.

**Solution**: The connector continuously polls Rx/Tx optical power and SFP power thresholds on the Uplink Optical table.

**Benefit**: NOC operators can spot a degrading uplink and dispatch a technician before it causes a customer-facing outage.

### Centralized GPON Access-Network Monitoring

**Challenge**: GPON access infrastructure from multiple vendors is hard to monitor consistently from a single pane of glass.

**Solution**: The connector exposes GPON/XGS-PON channels and PON interface status as standard DataMiner tables, alongside chassis health.

**Benefit**: Operators get a consistent, vendor-agnostic view of GPON access health inside DataMiner, without switching to the vendor's own EMS.

### Hardware-Health Early Warning

**Challenge**: Board or power-module failures on an OLT chassis can take down service for many subscribers at once.

**Solution**: The connector polls board temperature, board power, and power module tables on a regular timer.

**Benefit**: Hardware issues are surfaced early, reducing the blast radius of an unplanned chassis failure.

## Technical Reference

### Prerequisites

- **DataMiner** version **10.3.0.0 - 12752** or higher is required.
- **SNMPv2 connectivity** to the ZXA10 C600 chassis (community strings configured on the DataMiner element) is required.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_ZTE_ZXA10_C600_Technical).
