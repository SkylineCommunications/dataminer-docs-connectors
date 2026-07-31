---
uid: Connector_help_Rohde_Schwarz_FSV_Technical
---

# Rohde Schwarz FSV

## About

The Rohde Schwarz FSV is a signal and spectrum analyzer. This connector is a virtual connector that owns the device connection in C# using the Rohde & Schwarz RsInstrument (VISA) library, issuing SCPI commands to expose the device identity, current measurement settings, and live trace data in DataMiner.

> [!NOTE]
> This connector is a single-element virtual/SCPI (VISA) connector. It does not use SNMP and does not export child elements (DVEs).

## Configuration

### Connections

#### Virtual Connection

This connector is a virtual connector and has no port settings. The device connection is established from C# via the RsInstrument (VISA) library and is configured through the following parameters on the element:

- **Device IP Address**: The IP address/host of the device.
- **Device Port**: The IP port of the device, by default *5025* (used for the Raw Socket connection type).
- **Connection Type**: The VISA connection type used to reach the device:
  - **VXI-11** (*0*)
  - **Raw Socket** (*1*, default, port *5025*)
  - **HiSLIP** (*2*)

## How to Use

On the **Spectrum Analyzer** page, you can find DataMiner's default spectrum analysis component, showing the live trace data captured from the device. For more information on how to work with this, refer to [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

On the **General** page, you can find device information such as the Manufacturer, Model, Serial Number, and Firmware Version, together with the current measurement settings: start/stop/center frequency, span, reference level and scale, sweep time and points, resolution bandwidth (RBW), video bandwidth (VBW), and input attenuation. You can enter new values for these settings and apply them to the device. A toggle is available to enable or disable trace monitoring, which stops the periodic trace acquisition when only identity and settings are needed.

On the **Web Interface** page, you can open the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
