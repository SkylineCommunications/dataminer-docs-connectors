---
uid: Connector_help_Anywave_MHPTV_CTL-M
---

# Anywave MHPTV CTL-M

The **Anywave MHPTV CTL-M** connector enables real-time monitoring and remote control of Anywave MHPTV transmitters equipped with a **CTL-M controller** — the multi-PA variant designed for installations with three or more post amplifiers.

By integrating these transmitters into DataMiner, broadcast operators gain unified, continuous oversight of transmitter health, RF performance, and system configuration across distributed sites, without requiring on-site intervention for routine status checks or configuration changes.

## About

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [SLC Main] | Initial version | - | - |

### Product Info

| Range | Supported Firmware |
|--|--|
| 1.0.0.x | - |

### System Info

| Range | DCF Support | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | No | Yes | - | - |

## CTL-M vs. CTL-S: Choosing the Right Connector

Anywave MHPTV transmitters are offered with two controller variants. Selecting the correct DataMiner connector depends on the hardware controller installed in your device:

| Controller | Use Case | DataMiner Connector |
|--|--|--|
| **CTL-S** | Installations with **3 or fewer** post amplifiers | [Anywave MHPTV](xref:Connector_help_Anywave_MHPTV) |
| **CTL-M** | Installations with **more than 3** post amplifiers | Anywave MHPTV CTL-M (this connector) |

> [!IMPORTANT]
> Although both connectors monitor the same device family and share a common page layout, the underlying SNMP OID structure differs between controllers. Using the wrong connector for your hardware will result in failed polls and missing data. Verify the controller model installed in your transmitter before creating elements.

## Configuration

For detailed connection settings and page descriptions, see [Anywave MHPTV CTL-M Technical](xref:Connector_help_Anywave_MHPTV_CTL-M_Technical).

## Use Case: Centralized Transmitter Fleet Management

Broadcast facilities managing MHPTV transmitters across multiple transmission sites can use DataMiner to consolidate monitoring into a single operations center. The connector surfaces all critical RF metrics — forward and reflected power, VSWR, rejected amplifier power — alongside configurable alarm thresholds that notify operators of degraded performance before signal quality is impacted.

Remote configuration access through the System Configuration page allows operators to adjust AGC settings, exciter parameters, and transmit state without dispatching field engineers, reducing operational costs and response time for routine interventions.
