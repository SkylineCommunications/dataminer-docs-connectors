---
uid: Connector_help_Terrasat_Communications_IBUC_1+2_Tx_Redundant_System
---

# Terrasat Communications IBUC 1+2 Tx Redundant System

## About

The **Terrasat Communications IBUC 1+2 Tx Redundant System** connector monitors and manages a Terrasat 1+2 transmit redundant BUC (Block Up Converter) system through its redundancy controller. Using an SNMP connection, it provides real-time visibility into the controller unit, the individual BUCs (A, B, and Spare), the redundancy switching status, and the associated alarms and sensor readings.

## Key Features

- **Controller monitoring**: Retrieves controller information such as model number, serial number, firmware version, hardware version and the internal 10 MHz reference status.

- **Per-BUC insight**: Displays dedicated information, as well as alarm and sensor tables for each BUC (A, B, and Spare), including power, frequency band, temperature, and input/output power levels.

- **Redundancy management**: Displays the switching type and the A/B switch positions so the redundancy state of the system can be followed and configured.

- **Alarm monitoring**: Surfaces controller and per-BUC alarms such as faulted BUCs, switch faults, 10 MHz alarms, voltage-level alarms and BUC-offline conditions.

- **Sensor readings**: Reports supply voltage, 10 MHz level, and per-BUC sensor values (supply voltage/current, DRO voltage, temperature, and power levels).

## Use Cases

### Maintaining Transmit Uptime with Redundancy Awareness

**Challenge**: Operators must guarantee continuous transmission and know immediately which BUC is active and whether the spare is healthy.

**Solution**: The connector continuously polls the redundancy controller, exposing the switch positions, switching type, and per-BUC status in DataMiner.

**Benefit**: Faster awareness of redundancy state and switchovers, reducing the risk of unnoticed loss of transmit capability.

### Early Detection of BUC Degradation

**Challenge**: Gradual degradation of a BUC (temperature rise, power drift, supply issues) can lead to failures if not caught early.

**Solution**: Per-BUC sensor and alarm tables are monitored in real time, with alarms triggered when thresholds for temperature, input/output power, and supply values are exceeded.

**Benefit**: Proactive maintenance and fewer unplanned outages by acting on early warning signals.

### Centralized Monitoring of the Satellite Uplink Chain

**Challenge**: Satellite uplink equipment is often distributed and monitored through separate tools.

**Solution**: The connector integrates the Terrasat redundant BUC system into DataMiner alongside the rest of the uplink chain.

**Benefit**: The uplink infrastructure can be monitored from a single pane of glass, simplifying operations and troubleshooting.

## Technical Reference

### Prerequisites

- **SNMP access** to the redundancy controller is needed to poll the controller, BUC, alarm, and sensor data.

- **SNMP community strings** are needed to read from and write to the device.

- **A compatible DataMiner version** is required (minimum version 10.4.0.0).

### Connections

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *161*).
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The device web interface is accessible from the **Web Interface** page (`http://[Polling IP]/`) when the client machine has network access to the product.
