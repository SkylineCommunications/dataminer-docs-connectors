---
uid: Connector_help_Rohde_Schwarz_FSC3
---

# Rohde Schwarz FSC3

## About

The Rohde Schwarz FSC3 connector allows seamless integration of the R&S FSC3 spectrum analyzer into DataMiner. It provides real-time access to spectrum trace data and instrument information over a virtual connection driven by the Rohde & Schwarz RsInstrument (VISA) library, making it easy to monitor measurements, adjust analyzer settings, and automate RF signal workflows from a single interface.

## Key Features

- **Real-time spectrum analysis**: View live trace data from the analyzer directly in DataMiner's spectrum analysis component.
- **Instrument identification**: View key device details to verify the connected analyzer and its current software state.
- **Measurement control**: Remotely adjust core analyzer settings to quickly adapt the device to changing operational needs.
- **Trace monitoring toggle**: Enable or disable trace monitoring to reduce load when only identity and settings are needed.

## Use Cases

### RF Monitoring

**Challenge**: Operators need to keep an eye on RF spectrum measurements without standing at the instrument front panel.

**Solution**: Integrate the FSC3 into DataMiner to stream live trace data and instrument status to a central interface.

**Benefit**: Enables continuous, remote spectrum monitoring alongside the rest of the monitored infrastructure.

### Remote Measurement Setup

**Challenge**: Engineers need to change measurement parameters (frequency, span, bandwidths, reference level) on a remote analyzer.

**Solution**: Use the connector's write settings to push measurement configuration to the device and read the applied values when data is next polled.

**Benefit**: Removes the need for physical access and speeds up measurement reconfiguration.

### Automated Signal Analysis

**Challenge**: Repetitive sweeps and trace capture are time-consuming to run manually.

**Solution**: Drive the analyzer from DataMiner to automate sweep acquisition and collect trace data.

**Benefit**: Increases efficiency and ensures consistent, repeatable data collection.

## Technical Reference

The device connection is configured through the element's IP address, port, and connection type (VXI-11, Raw Socket (default, port 5025), or HiSLIP).

> [!NOTE]
> For detailed configuration and usage instructions, refer to the [technical documentation](xref:Connector_help_Rohde_Schwarz_FSC3_Technical).
