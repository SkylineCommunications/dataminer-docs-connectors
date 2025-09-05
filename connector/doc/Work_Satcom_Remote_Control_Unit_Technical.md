---
uid: Connector_help_Work_Satcom_Remote_Control_Unit_Technical
---

# Work Satcom Remote Control Unit

## About

This connector monitors and controls a Work Satcom Remote Control Unit and up to eight connected converters. It exposes controller status, addressing, UPC functionality, and per‑converter configuration such as frequency, attenuation, and equalization.

## Configuration

### Connections

This connector is implemented as a serial protocol.

- Serial connection
  - Configure the serial COM port or serial‑over‑IP gateway according to your deployment.
  - Typical settings (baud rate, parity, etc.) should match the device manual.

- TCP/Serial gateway (optional)
  - If using serial‑over‑IP, specify the gateway IP/host and port during element creation.

### Pages and Parameters

- General
  - Controller Alarm Status (discreet)
  - IP Address, Subnet Mask, Gateway, TCP Port (read-only)
  - Frequency Limit Minimum/Maximum (GHz)
  - Alarm Relay Inhibit (toggle)

- Unit Address
  - Channel/Unit selector (1–8)
  - Unit Address (None, @, A–Z)
  - Configure button to apply addressing

- Unit Overview
  - Table listing units 1–8 with per‑unit general alarm status

- UPC
  - UPC Master Control (On/Off)
  - Clear Sky Calibration (V)
  - Deep Fade Timer (s), Deep Fade Enable Timer (s)
  - Deep Fade Threshold (dB)
  - Power Control Cycle (s)
  - Voltage per 1 dB Attenuation (V)
  - Restart Deep Fade Timer
  - Downlink Fade (current dB), Downlink Fade Alarm (discreet)
  - Beacon Receiver Voltage (V)

- Converter 1 … Converter 8
  - Unit Status (discreet)
  - Reference Source (Internal/External/Auto)
  - Frequency (GHz)
  - Gain (On/Off)
  - External Mute (Enabled/Disabled)
  - Warmup Mute Time (Normal/Short)
  - Attenuation (dB)
  - Equalization (dB/GHz)
  - UPC controls (Power Control, Minimum Attenuation, Uplink/Downlink Ratio, Deep Fade Behavior)

## How to Use

- Start on General to validate controller status and basic limits.
- Use Unit Address to assign addresses to channels; then verify Unit Overview alarms.
- Configure UPC behavior on the UPC page to match link fade compensation strategy.
- For each converter page, set Frequency, Attenuation, Equalization, and related controls. Monitor Unit Status and communication alarms.

## Alarms

- Discreet statuses (e.g., Controller Alarm Status, Unit Status, Downlink Fade Alarm) and numeric thresholds generate alarms based on protocol definitions.
- “Address Not Configured,” communication issues, warmup, and frequency limit violations are explicitly indicated.