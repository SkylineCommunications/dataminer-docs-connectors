---
uid: Connector_help_Agilent_N9010A-526_EXA
---

# Agilent N9010A-526 EXA

## About

The Agilent N9010A-526 EXA connector allows seamless integration of the Agilent (Keysight) N9010A EXA
signal analyzer into DataMiner. It provides real-time access to spectrum trace data and instrument
information over a **virtual (VISA) connection** driven by the Rohde & Schwarz RsInstrument library,
making it easy to monitor measurements, adjust analyzer settings, and automate RF signal workflows from
a single interface. The N9010A-526 option covers a **9 kHz to 26.5 GHz** frequency range. The device
connection is configured through the element's **Device IP Address**, **Device Port** and
**connection type** (VXI-11, Raw Socket or HiSLIP).

## Key Features

- **Real-time spectrum analysis**: View live trace data from the analyzer directly in DataMiner's spectrum analysis component.
- **Instrument identification**: Read the Manufacturer, Model, Serial Number, and Firmware Version of the connected device.
- **Measurement control**: Configure start/stop/center frequency, span, reference level and scale, sweep time and points, resolution bandwidth (RBW), video bandwidth (VBW), and input attenuation — including their AUTO modes.
- **Sweep mode**: Select Single or Continuous sweep directly from DataMiner.
- **Zero-span sweep**: Start a zero-span, time-adjusted rolling trace acquisition on demand.
- **Preset**: Restore the instrument's default settings from DataMiner with a confirmation-guarded button.
- **Flexible connectivity**: Connect over VISA using VXI-11, Raw Socket (default, port 5025) or HiSLIP.

## Use Cases

### RF Monitoring

**Challenge**: Operators need to keep an eye on RF spectrum measurements without standing at the instrument front panel.

**Solution**: Integrate the N9010A EXA into DataMiner to stream live trace data and instrument status to a central interface.

**Benefit**: Enables continuous, remote spectrum monitoring alongside the rest of the monitored infrastructure.

### Remote Measurement Setup

**Challenge**: Engineers need to change measurement parameters (frequency, span, bandwidths, reference level, sweep time, attenuation) on a remote analyzer.

**Solution**: Use the connector's write settings to push measurement configuration to the device over the VISA connection and read the applied values back on the next poll.

**Benefit**: Removes the need for physical access and speeds up measurement reconfiguration.

### Automated Signal Analysis

**Challenge**: Repetitive sweeps and trace capture are time-consuming to run manually.

**Solution**: Drive the analyzer from DataMiner to automate sweep acquisition and collect trace data.

**Benefit**: Increases efficiency and ensures consistent, repeatable data collection.

## Technical Reference

The device connection is configured through the element's IP address, port, and connection type (VXI-11, Raw Socket (default, port 5025), or HiSLIP).

> [!NOTE]
> For detailed configuration and usage instructions, refer to the [technical documentation](xref:Connector_help_Agilent_N9010A-526_EXA_Technical).

