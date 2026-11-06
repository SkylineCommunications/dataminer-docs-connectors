---
uid: Connector_help_Rohde_Schwarz_FSP30
description: "Monitor and control Rohde Schwarz FSP30 spectrum analyzers in DataMiner with live traces, remote measurement settings, and RF frequency translation."
---

# Rohde Schwarz FSP30

## About

The Rohde Schwarz FSP30 connector integrates the R&S FSP30 spectrum analyzer (9 kHz to 30 GHz) into DataMiner. It sends SCPI commands to the analyzer over a GPIB bus or an RS-232 link, and shows the live trace in the DataMiner Spectrum Analysis module. Operators can follow RF measurements and change the analyzer settings from one central interface, without access to the front panel.

## Key Features

- **Live spectrum traces**: View the analyzer trace in the DataMiner Spectrum Analysis module, with 125 to 8001 points per trace.
- **Remote measurement control**: Change the center, start, and stop frequency, span, reference level and scale, resolution and video bandwidth, sweep time, input attenuation, detector, and scale type.
- **Automatic modes**: Leave the resolution bandwidth, video bandwidth, sweep time, and input attenuation in automatic mode, and see the value that the analyzer selected.
- **RF frequency translation**: When a frequency converter is placed in front of the analyzer, enter an LO offset and LO side. You then see and set RF frequencies, while the connector tunes the analyzer to the converted frequency.
- **Safe frequency changes**: When an LO offset is set, frequencies outside the analyzer range are rejected and logged instead of being sent.
- **Device error reporting**: The analyzer error queue is read after every settings change, and errors are logged.
- **Measurement inhibit**: Stop all DataMiner measurements on the analyzer during maintenance, with one setting.

## Use Cases

### Remote RF Spectrum Monitoring

**Challenge**: Operators need to follow RF spectrum measurements without being at the instrument.

**Solution**: Integrate the FSP30 into DataMiner to show the live trace and the analyzer settings in the Spectrum Analysis module.

**Benefit**: Continuous, remote spectrum monitoring alongside the rest of the monitored infrastructure.

### Monitoring Behind a Frequency Converter

**Challenge**: The analyzer measures an IF or L-band signal, but operators think and work in RF frequencies.

**Solution**: Enter the LO offset and LO side of the converter on the element. The connector translates all frequencies between RF and the analyzer input.

**Benefit**: Operators work in RF only, and do not have to calculate the analyzer frequency themselves.

### Remote Measurement Setup

**Challenge**: Engineers need to change measurement settings on a remote analyzer.

**Solution**: Apply new settings from the Spectrum Analysis module or from an automation script. The connector reads the applied values back from the analyzer.

**Benefit**: No physical access is needed, and measurement changes are faster.

## Technical Reference

### Prerequisites

- DataMiner **10.4.0.0** (build 14003) or later for range 3.1.0.x.
- An R&S FSP30 that the DataMiner Agent can reach over GPIB (recommended) or RS-232. The connector uses a serial connection: a GPIB bus address, or a COM port for RS-232. Connecting to the analyzer over LAN by IP address is not supported.

> [!NOTE]
> For detailed configuration and usage instructions, refer to the [technical documentation](xref:Connector_help_Rohde_Schwarz_FSP30_Technical).
