---
uid: Connector_help_HW_Group_Temp_232_Technical
---

# HW Group Temp-232

## About

This connector processes temperature data reported by the HW Group Temp-232 device in auto‑report mode over a Smart-Serial connection. It parses the incoming frames and updates a single Temperature parameter, enabling alarming and trending in DataMiner.

## Configuration

### Connections

#### Smart-Serial Connection

This connector uses a Smart-Serial connection and requires one of the following during element creation:

- Direct serial (RS-232): Select the COM port on the DataMiner Agent.
- Serial-over-IP: Provide the host/IP and TCP port of the serial device server.

Notes:

- The device must be configured to output periodic temperature frames (auto-report mode).
- No authentication or session commands are used by this connector.

## How to Use

- Open the element and navigate to the Temperature page to see the real-time temperature reading.
- The Temperature parameter:
  - Units: deg C
  - Decimals: 1
  - Range: -55 to +125
  - Alarming: Enabled (threshold-based)