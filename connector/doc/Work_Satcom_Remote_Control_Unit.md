---
uid: Connector_help_Work_Satcom_Remote_Control_Unit
---

# Work Satcom Remote Control Unit

## About

The Work Satcom Remote Control Unit connector integrates Work Satcom controllers with DataMiner. It provides monitoring and control for up to eight converters via the controller, including controller status, unit addressing, Uplink Power Control (UPC), and per‑converter operational parameters (e.g., frequency, attenuation, equalization, gain, mute).

## Key Features

- Controller overview
  - Controller alarm state, alarm relay inhibit, IP/network information, min/max system frequency limits.
- Unit overview and addressing
  - Unit Address page to map channels to device addresses (None, @, A–Z).
  - Unit Overview table summarizing per‑unit alarms for channels 1–8.
- UPC page
  - Master Control, Clear Sky Calibration, Deep Fade timers/threshold, Uplink/Downlink ratio, Minimum Attenuation, Downlink Fade indicators, Beacon Receiver voltage.
- Per‑converter pages (1–8)
  - Reference Source, Frequency (GHz), Attenuation (dB), Equalization (dB/GHz), Gain, External Mute, Warmup Mute Time, and UPC controls.
- Automatic alarm generation
  - Discreet status parameters and numeric thresholds as defined in the protocol drive alarms.

## Use Cases

### Use Case 1: Multi‑Converter Supervision

- Monitor controller and each converter’s alarms, frequency, attenuation, and mute state on a single view to quickly identify issues.

### Use Case 2: Weather Fade Compensation

- Use UPC features (Deep Fade detection, ratios, timers) to automatically compensate uplink power during downlink fades.

### Use Case 3: Safe Operations and Addressing

- Configure Unit Address per channel and verify "Address Not Configured", Warmup, and Communication alarms to prevent misrouting and unsafe transmissions.

## Technical Reference

### Prerequisites

- DataMiner 10.3.0 or higher.

> [!NOTE]
> For detailed technical information, see the [technical reference](xref:Connector_help_Work_Satcom_Remote_Control_Unit_Technical).
