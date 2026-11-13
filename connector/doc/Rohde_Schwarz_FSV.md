---
uid: Connector_help_Rohde_Schwarz_FSV
description: "Monitor and control Rohde & Schwarz FSV spectrum analyzers in DataMiner with live spectrum traces, RF frequency translation, and VISA connectivity."
---

# Rohde Schwarz FSV

## About

The Rohde Schwarz FSV connector brings the R&S FSV signal and spectrum analyzer family into DataMiner. You can follow live spectrum traces, check the instrument identity, and change measurement settings from DataMiner instead of at the front panel.

When the analyzer measures the L-band or IF output of a downconverter, the connector can work in RF frequencies. You see and enter RF values, and the connector tunes the analyzer to the matching L-band or IF frequency.

## Key Features

- **Live spectrum traces**: Show the analyzer trace in DataMiner Spectrum Analysis.
- **Remote measurement control**: Set the center, start, and stop frequency, span, reference level and scale, resolution and video bandwidth, sweep time, sweep points, and input attenuation. Bandwidths, sweep time, and attenuation can also be set to *Auto*.
- **RF frequency translation**: Enter the local oscillator (LO) frequency and side of the downconverter, and work in RF frequencies while the analyzer stays tuned in L-band or IF.
- **Frequency range protection**: Frequencies outside the range of the connected FSV model are rejected and logged instead of being sent to the instrument.
- **Detector selection**: See which trace detector is in use, and select a detector or let the analyzer choose.
- **Sweep and display control**: Switch between single and continuous sweep, start a zero-span sweep on demand, and control the instrument display.
- **Preset**: Restore the default instrument settings from DataMiner.
- **Instrument identification**: View the manufacturer, model, serial number, firmware version, and installed options.
- **Flexible connectivity**: Connect over VISA with VXI-11, Raw Socket, or HiSLIP.

## Use Cases

### Remote RF Monitoring

**Challenge**: Operators need to follow RF spectrum measurements without standing at the instrument front panel.

**Solution**: Integrate the FSV into DataMiner to show live traces and instrument status in one central interface.

**Benefit**: Continuous, remote spectrum monitoring alongside the rest of the monitored infrastructure.

### Monitoring Signals Behind a Downconverter

**Challenge**: The analyzer measures the L-band output of an LNB or downconverter, but operators work with RF frequencies. Translating every value by hand is slow and error-prone.

**Solution**: Set the LO frequency and LO side on the element. Operators enter RF frequencies, and the connector tunes the analyzer to the matching L-band frequency and shows the trace on an RF axis.

**Benefit**: Fewer tuning errors, and no frequency translation needed in scripts or measurement points.

### Remote Measurement Setup

**Challenge**: Engineers need to change frequency, span, bandwidths, reference level, sweep time, or attenuation on a remote analyzer.

**Solution**: Change the settings in DataMiner. The connector sends them to the analyzer and reads back the values the analyzer applied.

**Benefit**: No physical access is needed, and measurements can be reconfigured faster.

## Technical Reference

### Prerequisites

- DataMiner **10.4.0.0 - 14003** or higher.
- A VISA library installed on every DataMiner Agent that hosts an element using this connector. VISA is not included in the connector package.

> [!NOTE]
> For detailed configuration and usage instructions, refer to the [technical documentation](xref:Connector_help_Rohde_Schwarz_FSV_Technical).
