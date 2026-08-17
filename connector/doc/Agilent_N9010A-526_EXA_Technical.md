---
uid: Connector_help_Agilent_N9010A-526_EXA_Technical
---

# Agilent N9010A-526 EXA

## About

The Agilent N9010A-526 EXA is a signal/spectrum analyzer from Agilent (Keysight). This connector communicates with the instrument over a virtual connection driven by the Rohde & Schwarz RsInstrument (VISA) library using SCPI commands, and exposes the device identity, current measurement settings, and live trace data in DataMiner. The N9010A-526 option covers a **9 kHz to 26.5 GHz** frequency range.

> [!NOTE]
> This connector is a single-element virtual/SCPI connector. It does not use SNMP and does not export child elements (DVEs).

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection. The device connection is configured through the following parameters on the **General** page of the element:

- **Device IP Address**: The IP address or host name of the device.
- **Device Port**: The IP port of the device. When set to *Auto*, the default port for the selected connection type is used (*5025* for Raw Socket).
- **Connection Type**: The Rohde & Schwarz connection protocol used to reach the device. The following options are supported:
  - **VXI-11**
  - **Raw Socket** (default)
  - **HiSLIP**

## How to Use

On the **Spectrum Analyzer** page, you can find DataMiner's default spectrum analysis component, showing the live trace data captured from the device. For more information on how to work with this, refer to [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

On the **General** page, you can find device information such as the Manufacturer, Model, Serial Number, and Firmware Version, together with the current measurement settings: start/stop/center frequency, span, reference level and scale, sweep time and points, resolution bandwidth (RBW), video bandwidth (VBW), and input attenuation. You can enter new values for these settings and apply them to the device. Where supported, the RBW, VBW, sweep time, and attenuation parameters can be set to their **AUTO** mode.

The **General** page also provides the following controls:

- **Sweep Mode**: Select *Single* or *Continuous* sweep acquisition.
- **Zero-Span Sweep**: Start a zero-span, time-adjusted rolling trace acquisition on demand.
- **Preset**: Reset the instrument to its default measurement state. This action is guarded by a confirmation prompt.

