---
uid: Connector_help_Rohde_Schwarz_FSV
---

# Rohde Schwarz FSV

## About

The Rohde Schwarz FSV connector allows seamless integration of the R&S FSV signal and spectrum analyzer into DataMiner. It provides real-time access to spectrum trace data and instrument information over a virtual connection driven by the Rohde & Schwarz RsInstrument (VISA) library, making it easy to monitor measurements, adjust analyzer settings, and automate RF signal workflows from a single interface. The device connection is configured through the element's Device IP Address, Device Port and connection type (VXI-11, Raw Socket or HiSLIP).

## Key Features

- **Real-time spectrum analysis**: View live trace data from the analyzer directly in DataMiner's spectrum analysis component.
- **Instrument identification**: Read the Manufacturer, Model, Serial Number, and Firmware Version of the connected device.
- **Measurement control**: Configure start/stop/center frequency, span, reference level and scale, sweep time and points, resolution bandwidth (RBW), video bandwidth (VBW), and input attenuation.
- **Trace monitoring toggle**: Enable or disable trace monitoring to reduce load when only identity and settings are needed.
- **Flexible connectivity**: Connect over VISA using VXI-11, Raw Socket (default, port 5025) or HiSLIP.

## Use Cases

### RF Monitoring

**Challenge**: Operators need to keep an eye on RF spectrum measurements without standing at the instrument front panel.

**Solution**: Integrate the FSV into DataMiner to stream live trace data and instrument status to a central interface.

**Benefit**: Enables continuous, remote spectrum monitoring alongside the rest of the monitored infrastructure.

### Remote Measurement Setup

**Challenge**: Engineers need to change measurement parameters (frequency, span, bandwidths, reference level) on a remote analyzer.

**Solution**: Use the connector's write settings to push measurement configuration to the device and read the applied values back on the next poll.

**Benefit**: Removes the need for physical access and speeds up measurement reconfiguration.

### Automated Signal Analysis

**Challenge**: Repetitive sweeps and trace capture are time-consuming to run manually.

**Solution**: Drive the analyzer from DataMiner to automate sweep acquisition and collect trace data.

**Benefit**: Increases efficiency and ensures consistent, repeatable data collection.

## Technical Reference

> [!NOTE]
> For detailed configuration and usage instructions, refer to the [technical documentation](xref:Connector_help_Rohde_Schwarz_FSV_Technical).
