---
uid: Connector_help_Vertex_7134_Technical
---

# Vertex 7134

## About

This is a DataMiner connector for the Vertex 7134 antenna control unit (ACU). It supports step tracking and memory tracking, and it allows you to position the antenna manually or through a predefined value stored in a table as a preset.

## Configuration

### Connections

#### Serial Connection

This is a serial connector that communicates with the device through a serial gateway. When you create the element, configure the following:

- **IP address/host**: The IP address of the serial gateway that connects to the device.
- **IP port**: The IP port of the serial gateway.

These communication settings are used to send commands to and receive responses from the device.

## How to Use

### Main View

This page displays general information about the unit.

### General

This page displays more detailed information about the unit, along with a large number of statuses.

### Positions

This page allows you to set manual positioning of the antenna and to configure the target and program tables.

### Step Track

This page provides the **Step Track** parameters and sets.

### Memory Track

This page provides the enhanced memory track parameters and sets.

### Alarms

This page displays all alarms that can be present on the unit. Monitoring is enabled for these parameters.

## Notes

- As this is a serial connector, a connection to a real device is required.
- Step track and enhanced memory track are only supported on the 7134 EMT device. Before you start memory tracking, set the correct track parameters. The targets (A, B, C) used when setting the track parameters must be present in the target table.
- To control the device from DataMiner, the device must be in **Remote Control Mode** (RS-232/422 Remote Control or Remote Mode), not in **Local** mode.
- If the serial gateway is configured at a slow 1.2 kbaud rate (RS-232), the Target Azimuth, Polarization, or Elevation settings may not work correctly in the **Target** table. If the serial gateway is configured to RS-428, these settings work correctly.
