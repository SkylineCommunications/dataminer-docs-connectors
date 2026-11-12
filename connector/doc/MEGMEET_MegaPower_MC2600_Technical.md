---
uid: Connector_help_MEGMEET_MegaPower_MC2600_Technical
---

# MEGMEET MegaPower MC2600

## About

The **MEGMEET MegaPower MC2600** connector monitors a MegaPower MC2600 power supply controller over SNMP. It focuses on power-system telemetry and module-level measurements used for operational monitoring and alarming.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

- **IP address/host**: The management IP or hostname of the MC2600 controller.
- **IP port**: The SNMP port of the device (default: 161).
- **Bus address**: Not required.

## How to Use

### General

The General page provides system-level monitoring values, including:

- **System Description** and **System Object ID** for device identification.
- **System up Time** and **System Last Change** for availability tracking.
- **System OR** fields for supported SNMP object registration details.

From this page, the **Device Info** page button opens a subpage with product and platform details such as:

- **Product Name** and **Product Model**.
- **Firmware Version** and **Site Name**.
- **SNMP Version**, **System Rectifier Type**, and **System Solar Type**.
- **Battery Current** for load monitoring.

### Modules

The Modules page contains the **Modules** table, which presents per-module performance and state information:

- **Input Voltage** and **Output Voltage**.
- **Output Current** and **Power**.
- **Temperature** with alarm thresholds.
- **Status** (e.g., ON/OFF).

Use this table to identify module-level imbalance, overheating, or output anomalies.
