---
uid: Connector_help_Rohde_Schwarz_FSL3
---

# Rohde Schwarz FSL3

## About

The Rohde Schwarz FSL3 connector integrates the R&S FSL3 spectrum analyzer into DataMiner over a
**virtual (VISA) connection** driven by the Rohde & Schwarz RsInstrument library. It provides
real-time access to the analyzer's primary spectrum trace and instrument settings, making it easy to
monitor measurements, adjust analyzer parameters, and automate RF signal workflows from a single
interface. The device connection is configured through the element's **Device IP Address**,
**Device Port** and **connection type** (VXI-11, Raw Socket or HiSLIP).

## Key Features

- **Real-time spectrum analysis**: Decode the analyzer's primary trace (IEEE-754 float block) into a level series and surface it as a DataMiner spectrum measurement.
- **Instrument identification**: Read the Manufacturer, Model, Serial Number, and Firmware Version of the connected device.
- **Measurement control**: Configure center/start/stop frequency and span, reference level and scale, resolution bandwidth (RBW), video bandwidth (VBW), sweep time, input attenuation, detection mode, scale type, and amplitude units — including their AUTO modes.
- **Flexible connectivity**: Connect over VISA using VXI-11, Raw Socket (default, port 5025) or HiSLIP.
- **Sweep mode**: Select Single or Continuous sweep (`:INIT:CONT`) directly from DataMiner.
- **Zero-span sweep**: Start a zero-span, time-adjusted rolling trace acquisition on demand (ported from the R&S FSV/FSC3 connectors).
- **Preset**: Restore the instrument's default settings from DataMiner with a confirmation-guarded button (`*RST`, ported from the R&S FSV/FSC3 connectors).
- **Sweep & timeout safeguards**: Single-sweep and timeout coordination prevents a stalled instrument from hanging the poll chain.

## Use Cases

### RF Monitoring

**Challenge**: Operators need to keep an eye on RF spectrum measurements without standing at the instrument front panel.

**Solution**: Integrate the FSL3 into DataMiner to stream the live primary trace and instrument status to a central interface.

**Benefit**: Enables continuous, remote spectrum monitoring alongside the rest of the monitored infrastructure.

### Remote Measurement Setup

**Challenge**: Engineers need to change measurement parameters (frequency, span, bandwidths, reference level, sweep time, attenuation) on a remote analyzer.

**Solution**: Use the connector's write settings to push measurement configuration to the device over the VISA connection and read the applied values back on the next poll.

**Benefit**: Removes the need for physical access and speeds up measurement reconfiguration.

### Automated Signal Analysis

**Challenge**: Repetitive sweeps and trace capture are time-consuming to run manually.

**Solution**: Drive the analyzer from DataMiner to automate sweep acquisition and collect decoded trace data.

**Benefit**: Increases efficiency and ensures consistent, repeatable data collection.

## Technical Reference

The device connection is configured through the element's IP address, port, and connection type (VXI-11, Raw Socket (default, port 5025), or HiSLIP).

> [!NOTE]
> For detailed configuration and usage instructions, refer to the [technical documentation](xref:Connector_help_Rohde_Schwarz_FSL3_Technical).
