---
uid: Connector_help_Calian_Multiport_Decimator
description: "Monitor and control Calian Multiport Decimator D4 spectrum analyzers in DataMiner with live traces, RF port switching, and per-port converter offsets."
---

# Calian Multiport Decimator

## About

The Calian Multiport Decimator connector integrates the Calian Multiport Decimator D4 spectrum analyzer into DataMiner. The D4 has 4 or 8 RF inputs behind an internal switch, so one analyzer can monitor several RF paths, e.g., satellite feeds behind down converters. The connector shows the live trace of the selected input in the DataMiner Spectrum Analysis module, and lets operators select the input, change the measurement settings, and follow the health of the device from one interface.

## Key Features

- **Live spectrum traces**: View the trace of the active input in the DataMiner Spectrum Analysis module. Incomplete or invalid traces are discarded, so the last valid trace stays visible.
- **Multiport switching**: Select the active RF input and view the port names of the device.
- **Per-port down converter offset**: Enter the down converter offset of each input once. The connector then shows and accepts RF frequencies for the active input.
- **Measurement control**: Change the center frequency, span, resolution bandwidth (RBW), video bandwidth (VBW), detector (Peak or Average), and input attenuation, with automatic RBW and VBW modes.
- **Safe frequency changes**: Frequency settings are checked against the limits reported by the device before they are sent. Invalid requests are rejected and logged.
- **Robust sessions**: After a reconnection or a device reset, the connector sends its settings to the device again.
- **Device health**: Monitor the device status, temperature, calibration status, power supply voltages, and the last device error.
- **Support tools**: A Debug page with a read-only command console and trace statistics helps to investigate trace issues.

## Use Cases

### Satellite Carrier Monitoring

**Challenge**: Operators need to check carriers on several satellite feeds, each behind its own down converter.

**Solution**: Connect the feeds to the D4 inputs, enter the down converter offset of each input, and switch between inputs from DataMiner.

**Benefit**: One analyzer covers several RF paths, and operators always work in RF frequencies.

### Remote Spectrum Checks

**Challenge**: Engineers need to look at the spectrum of a remote site without traveling to it.

**Solution**: Use the Spectrum Analysis module to request traces and change the measurement settings on the D4.

**Benefit**: Faster troubleshooting of carrier and interference issues from a central location.

## Technical Reference

### Prerequisites

- DataMiner **10.4.0.0** (build 14003) or later.
- A Calian Multiport Decimator D4 with the legacy socket API enabled, reachable from the DataMiner Agent over TCP/IP. The connector uses this API on TCP port 9784.

> [!NOTE]
> For detailed configuration and usage instructions, refer to the [technical documentation](xref:Connector_help_Calian_Multiport_Decimator_Technical).
