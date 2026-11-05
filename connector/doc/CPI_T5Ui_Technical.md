---
uid: Connector_help_CPI_T5Ui_Technical
---

# CPI T5Ui

## About

This connector is designed to monitor and control the activity of the **CPI T5Ui** device.

The connector uses serial communication to allow the end user to control and monitor the device.

## Configuration

### Connections

#### Serial Connection — Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The IP address of the device.
- **IP port**: The IP port of the device.
- **Bus address**: The bus address of the device.

## How to Use

The **General** page provides access to essential device settings, including configurable low and high RF alarm and fault setpoints, as well as linearizer parameters for fine-tuning performance.

The **Control RF Output** page provides parameters for managing the device's RF output, including power levels in both dBm and watt. It also includes settings for ALC (Automatic Level Control) output power, displayed in both dBm and watt.

The **Meter Query** page displays key diagnostic parameters such as helix voltage, helix current, reflected RF, beam current, and attenuator value.

The **Status Info** page provides communication diagnostics, including parameters such as CMPA messages sent to the CIF, CMPA messages lost by the CIF, characters received by the CIF, and the latest CIF response message
