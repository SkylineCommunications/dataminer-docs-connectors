---
uid: Connector_help_Rohde_Schwarz_FSL18
description: "Monitor Rohde Schwarz FSL18 spectrum analyzers in DataMiner with live trace data, RF frequency translation, and VISA connectivity."
---

# Rohde Schwarz FSL18

## About

The Rohde Schwarz FSL18 connector brings the R&S FSL18 spectrum analyzer (9 kHz to 18 GHz) into DataMiner. You can view live traces in the DataMiner Spectrum Analysis module, change the analyzer settings remotely, and monitor the health of the analyzer from one place.

The connector connects to the analyzer over the network through VISA. It offers the same features and parameters as the [Rohde Schwarz FSL3](xref:Connector_help_Rohde_Schwarz_FSL3) connector, with ranges and limits tailored to the FSL18.

## Key Features

- **Live spectrum traces**: View and control the analyzer from the [DataMiner Spectrum Analysis module](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements), including spectrum presets and measurement scripts.
- **Work in RF frequencies**: When the analyzer measures the output of an LNB or downconverter, enter the LO frequency once. You then see and set all frequencies in RF, while the connector tunes the analyzer in L-band or IF.
- **Protection against invalid settings**: Frequency, attenuation, reference level, and sweep point settings outside the range of the FSL18 are rejected and logged before anything is sent to the device.
- **Analyzer health**: Monitor IF overload and the status of the external frequency reference, and trend them over time.
- **Device control**: Select the detector and the frequency reference, start a zero span sweep, switch between single and continuous sweep, and reset the analyzer with a preset.
- **Flexible connectivity**: Connect over VXI-11, Raw Socket, or GPIB through a LAN/GPIB gateway.

## Use Cases

### RF Monitoring

**Challenge**: Operators need to keep an eye on RF spectrum measurements without standing at the instrument front panel.

**Solution**: Integrate the FSL18 into DataMiner to view live traces and the analyzer status in a central interface.

**Benefit**: Continuous, remote spectrum monitoring alongside the rest of the monitored infrastructure.

### Remote Measurement Setup

**Challenge**: Engineers need to change measurement settings (frequency, span, bandwidths, reference level, sweep time, attenuation) on a remote analyzer.

**Solution**: Change the settings in the Spectrum Analysis module. The connector sends them to the analyzer and reads back the applied values.

**Benefit**: No physical access is needed, and measurements can be reconfigured quickly.

### Satellite Downlink Monitoring

**Challenge**: The analyzer measures an L-band signal, but operators think and work in RF frequencies. Converting every frequency by hand is slow and error-prone.

**Solution**: Configure the LO frequency and LO side of the downconverter on the element. Operators then enter and read RF frequencies directly.

**Benefit**: Fewer tuning mistakes, and spectrum presets that match the RF carrier plan.

## Technical Reference

### Prerequisites

- DataMiner 10.4.0.0 - 14003 or higher.
- A VISA library (R&S VISA or NI-VISA) on every DataMiner Agent that hosts an element.

The connection is configured with parameters on the **General** page of the element.

> [!NOTE]
> For detailed configuration and usage instructions, refer to the [technical documentation](xref:Connector_help_Rohde_Schwarz_FSL18_Technical).
