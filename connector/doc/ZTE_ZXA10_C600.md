---
uid: Connector_help_ZTE_ZXA10_C600
---

# ZTE ZXA10 C600

## About

The **ZTE ZXA10 C600** connector monitors ZTE ZXA10 C600 GPON OLT chassis via SNMPv2. It provides
visibility into chassis health, board and power status, uplink optical (SFP) status, and the
GPON/XGS-PON and Ethernet interfaces that deliver subscriber services — all from within DataMiner,
without relying on the vendor's own element management system.

## Key Features

- **Chassis & board health monitoring**: tracks board temperature, board power, power module, and
  CPU/system status so hardware issues are caught early.

- **Uplink optical monitoring**: reports Rx/Tx optical power on uplink SFPs, plus configurable SFP
  power thresholds, to catch optical degradation before it causes an outage.

- **GPON & XGS-PON service visibility**: models GPON interfaces, GPON channels, XGS-PON channels,
  and PON interface status, giving operators insight into subscriber-facing service health.

- **Ethernet interface monitoring**: standard and vendor-specific Ethernet interface status, rates,
  and bandwidth utilization.

- **LLDP neighbor discovery**: local port and remote-neighbor LLDP tables for topology awareness.

- **Configurable polling**: individual polling groups can be enabled or disabled to tune load on
  large deployments.

## Use Cases

### Proactive optical-link degradation detection

**Challenge**: Optical uplinks degrade gradually, and by the time a customer notices, service has
already been impacted.

**Solution**: The connector continuously polls Rx/Tx optical power and SFP power thresholds on the
Uplink Optical table.

**Benefit**: NOC operators can spot a degrading uplink and dispatch a technician before it causes a
customer-facing outage.

### Centralized GPON access-network monitoring

**Challenge**: GPON access infrastructure from multiple vendors is hard to monitor consistently
from a single pane of glass.

**Solution**: The connector exposes GPON/XGS-PON channels and PON interface status as standard
DataMiner tables, alongside chassis health.

**Benefit**: Operators get a consistent, vendor-agnostic view of GPON access health inside
DataMiner, without switching to the vendor's own EMS.

### Hardware-health early warning

**Challenge**: Board or power-module failures on an OLT chassis can take down service for many
subscribers at once.

**Solution**: The connector polls board temperature, board power, and power module tables on a
regular timer.

**Benefit**: Hardware issues are surfaced early, reducing the blast radius of an unplanned chassis
failure.

## Technical Reference

### Prerequisites

- **DataMiner** version `10.3.0.0 - 12752` or higher is required.
- **SNMPv2 connectivity** to the ZXA10 C600 chassis (community strings configured on the DataMiner
  element) is required.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_ZTE_ZXA10_C600_Technical).
