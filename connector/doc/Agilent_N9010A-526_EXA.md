---
uid: Connector_help_Agilent_N9010A-526_EXA
description: "Monitor Agilent (Keysight) N9010A-526 EXA analyzers in DataMiner with live traces, RF frequency translation, setting validation, and VISA connectivity."
---

# Agilent N9010A-526 EXA

## About

The Agilent N9010A-526 EXA connector brings the Agilent (Keysight) N9010A EXA signal analyzer with option 526 into DataMiner. You can view live traces in the DataMiner Spectrum Analysis module, change the analyzer settings remotely, and check the identity and options of the analyzer from one place.

The connector connects to the analyzer over the network through VISA and covers the full frequency range of option 526, from 10 Hz to 26.5 GHz.

## Key Features

- **Live spectrum traces**: View and control the analyzer from the [DataMiner Spectrum Analysis module](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements), including spectrum presets and spectrum scripts.
- **Work in RF frequencies**: When the analyzer measures the output of an LNB or downconverter, enter the LO frequency once. You then see and set all frequencies in RF, while the connector tunes the analyzer in L-band or IF.
- **Protection against invalid settings**: Settings outside the range of the N9010A are rejected before anything is sent to the device. The last rejected setting is shown on the element, so you can see why a change was not applied.
- **Device control**: Select the detector, start a zero span sweep, switch between single and continuous sweep, and reset the analyzer with a preset.
- **Flexible connectivity**: Connect over VXI-11, HiSLIP, or a raw socket on the LAN.
- **Built-in troubleshooting**: A Debug page shows the recent communication with the analyzer, to help find out why an element loses its connection.

## Use Cases

### RF Monitoring

**Challenge**: Operators need to keep an eye on RF spectrum measurements without standing at the instrument front panel.

**Solution**: Integrate the N9010A EXA into DataMiner to view live traces and the analyzer status in a central interface.

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
- A VISA library (e.g., Keysight IO Libraries, NI-VISA, or R&S VISA) on every DataMiner Agent that hosts an element.

The connection is configured with parameters on the **General** page of the element.

> [!NOTE]
> For detailed configuration and usage instructions, refer to the [technical documentation](xref:Connector_help_Agilent_N9010A-526_EXA_Technical).