---
uid: Connector_help_Work_Satcom_Remote_Control_Unit_Technical
---

# Work Satcom Remote Control Unit

## About

This connector monitors and controls a Work Satcom Remote Control Unit and up to eight connected converters. It exposes controller status, addressing, UPC functionality, and per‑converter configuration such as frequency, attenuation, and equalization.

## Configuration

### Connections

This connector is implemented as a serial protocol.

- Serial connection:

  - Configure the serial COM port or serial‑over‑IP gateway according to your deployment.
  - Typical settings (baud rate, parity, etc.) should match the device manual.

- TCP/serial gateway (optional):

  - If using serial‑over‑IP, specify the gateway IP/host and port during element creation.

## How to Use

Start on the **General** page to validate the controller status and basic limits.

Use the **Unit Address** parameter to assign addresses to channels, then verify the **Unit Overview** alarms.

Configure the UPC behavior on the **UPC** page to match link fade compensation strategy.

For each converter page, set the **Frequency**, **Attenuation**, **Equalization**, and related controls, and monitor the unit status and communication alarms.

## Alarms

- Discrete statuses (e.g. Controller Alarm Status, Unit Status, Downlink Fade Alarm) and numeric thresholds generate alarms based on protocol definitions.
- "Address Not Configured", communication issues, warmup, and frequency limit violations are explicitly indicated.
