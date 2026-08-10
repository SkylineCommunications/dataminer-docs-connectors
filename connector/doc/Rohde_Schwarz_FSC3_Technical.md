---
uid: Connector_help_Rohde_Schwarz_FSC3_Technical
---

# Rohde Schwarz FSC3

## About

The Rohde Schwarz FSC3 is a spectrum analyzer. This connector communicates with the instrument over a virtual connection driven by the Rohde & Schwarz RsInstrument (VISA) library using SCPI commands, and exposes the device identity, current measurement settings, and live trace data in DataMiner.

> [!NOTE]
> This connector is a single-element virtual/SCPI connector. It does not use SNMP and does not export child elements (DVEs).

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection. The device connection is configured through the following parameters on the **General** page of the element:

- **IP address/host**: The IP address or host name of the device.
- **Port**: The IP port of the device. When set to *Auto*, the default port for the selected connection type is used (*5025* for Raw Socket).
- **Connection Type**: The Rohde & Schwarz connection protocol used to reach the device. The following options are supported:
  - **VXI-11**
  - **Raw Socket** (default)
  - **HiSLIP**

## How to Use

On the **Spectrum Analyzer** page, you can find DataMiner's default spectrum analysis component, showing the live trace data captured from the device. For more information on how to work with this, refer to [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

On the **General** page, you can find device information such as the Manufacturer, Model, Serial Number, and Firmware Version, together with the current measurement settings: start/stop/center frequency, span, reference level and scale, sweep time and points, resolution bandwidth (RBW), video bandwidth (VBW), and input attenuation. You can enter new values for these settings and apply them to the device. A toggle button is available to enable or disable trace monitoring, which stops the periodic trace acquisition when only identity and settings are needed. A **Preset** button is also available to reset the instrument to its default measurement state.
