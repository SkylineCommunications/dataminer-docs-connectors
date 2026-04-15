---
uid: Connector_help_ND_Satcom_RCU_6000
---

# ND Satcom RCU 6000

## About

The **ND Satcom RCU 6000** is a Redundancy Controller Unit used in satellite ground station environments to manage High Power Amplifier (HPA) redundancy switching and monitoring. This connector communicates with the RCU 6000 via its HTTP REST API to provide real-time visibility into HPA status, alarm conditions, redundancy configuration, and switch positions.

## Key Features

- **HPA Monitoring**: Real-time tracking of all HPA operational parameters including TX mode, RF output power (dBm/W), attenuation, helix voltage/current, heater current, temperature, and linearizer gain.

- **HPA Alarm Surveillance**: Comprehensive alarm monitoring across 18 alarm indicators per HPA, covering RF inhibit, power supply faults, interlock conditions, temperature warnings, and EEPROM errors.

- **Redundancy Management**: Full visibility into the redundancy chain setup, including redundancy mode (Active/Blocked/Manual), switch status, last switched chain, and per-chain priority and mode configuration.

- **Transmit Chain Status**: At-a-glance operational status overview of all transmit chains, enabling quick identification of degraded or alarmed chains.

- **Notification Tracking**: Centralized event log capturing alarms, warnings, and informational messages from all managed devices with timestamps for historical analysis.

## Use Cases

### Automated Redundancy Monitoring

**Challenge**: Satellite ground station operators need continuous awareness of HPA redundancy status to ensure uninterrupted signal transmission. Manual monitoring of redundancy controllers is error-prone and slow.

**Solution**: The connector polls the RCU 6000 at configurable intervals, automatically detecting redundancy mode changes, switch positions, and last bypass commands. All redundancy chain configurations including priority levels are presented in a structured table view.

**Benefit**: Operators receive immediate alarm notifications when redundancy switching occurs or fails, reducing mean time to detect (MTTD) and ensuring rapid response to transmission path issues.

### HPA Health and Performance Tracking

**Challenge**: Managing multiple HPAs across a ground station requires tracking dozens of parameters per amplifier — from RF output power and attenuation to helix voltages and temperature — making manual oversight impractical.

**Solution**: The connector consolidates all HPA telemetry into organized table views, with separate pages for operational data, alarm states, RF limits, and setup configuration. Each parameter supports trending and alarm monitoring with configurable thresholds.

**Benefit**: Engineering teams gain a unified dashboard for all HPA health metrics, enabling predictive maintenance through trend analysis and reducing unplanned downtime.

### Multi-Device Station Overview

**Challenge**: Ground stations consist of multiple HPAs, switches, and power supplies that must all function correctly for reliable satellite communication. Correlating status across these devices is complex.

**Solution**: The connector maps the complete station topology — HPAs, switches, power supplies, and transmit chains — into a cohesive DataMiner element. The Station Configurator provides a high-level view of installed HPA types, while individual device tables offer drill-down detail.

**Benefit**: A single DataMiner element provides complete station visibility, simplifying operations and enabling cross-device alarm correlation through DataMiner's built-in correlation engine.

## Technical Reference

### Prerequisites

- **Network Connectivity**: HTTP access to the RCU 6000 REST API on the configured port (default: 9876).

- **DataMiner Version**: Minimum DataMiner version 10.4.0.0 - 14003 is required.

### Connections

This connector uses an **HTTP connection** to communicate with the RCU 6000 device.

| Setting         | Default Value |
|-----------------|---------------|
| IP port         | 9876          |
| Bus address     | ByPassProxy   |

### Web Interface

The web interface is only accessible when the client machine has network access to the product.
