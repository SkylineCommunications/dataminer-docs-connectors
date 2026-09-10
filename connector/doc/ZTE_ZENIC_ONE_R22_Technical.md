---
uid: Connector_help_ZTE_ZENIC_ONE_R22_Technical
description: "Configure and operate the ZTE ZENIC ONE R22 connector in DataMiner, including connections, polling controls, and alarm handling."
---

# ZTE ZENIC ONE R22 Technical

## About

The ZTE ZENIC ONE R22 is an intelligent management and control system for transport network environments.

This connector retrieves and correlates network inventory, performance, and alarm data from ZENIC ONE R22 by using SNMP and MTOSI polling workflows.

## Platform Information

The ZENIC ONE R22 platform information is provided below for deployment context:

- Software platform: x86 (Linux 64-bit), VMware 6.5 or higher, and TECS (OpenStack).
- Operating system: CGSL Linux v6 or higher.
- Database: PostgreSQL.

## Configuration

### Connections

This connector uses an SNMPv2 main protocol and an HTTP connection for MTOSI service polling.

During element setup, configure the SNMP and HTTP connection settings for your ZENIC ONE R22 deployment. After element creation, use the connector pages to complete polling credentials, polling targets, and interval settings.

### Connector Settings

Use the **Configuration** and **Redundancy Configuration** pages to configure the following runtime settings:

- Polling credentials: **Username** and **Password**.
- Polling intervals:
  - **Statistics Polling Interval**: default 120 seconds.
  - **Thresholds Polling Interval**: default 43200 seconds.
- Polling domain toggles:
  - **Query Managed Elements**
  - **Query Devices**
  - **Query Fan States**
  - **Query Termination Points**
  - **Query Laser Status**
  - **Query Current Performance**
  - **Query Performance Threshold**
- Redundancy and failover:
  - **Primary Server IP** and **Primary Server Port**
  - **Backup Server IP** and **Backup Server Port**
  - **Redundancy Switch Retries**

## How To Use

### General

Use this page to monitor connector state and synchronization details, including last polling timestamps, primary/backup target state, and alarm synchronization status. You can also start an alarm synchronization from this page.

### Nodes

This page displays the node inventory table with discovered managed elements and processing state information.

### Alarms

This page displays the current alarm source table and provides visibility into active alarm information.

### Alarms Manual

This page displays the consolidated alarm table and lets you maintain alarm table retention and cleanup controls.

### Redundancy Configuration

Use this page to configure primary and backup polling targets and retry behavior when failover is required.

### Configuration

Use this page to configure polling credentials, polling intervals, and per-domain polling enablement.

### Additional Monitoring Pages

Depending on the data available from your deployment, the connector provides additional pages for detailed operational views, including directional optical ports, optical channel and interface metrics, slot status, fan status, and termination points.

## Operational Notes

- The connector is primarily used for monitoring and synchronization.
- Starting alarm synchronization triggers a device-facing synchronization action.
