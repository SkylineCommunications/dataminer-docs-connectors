---
uid: Connector_help_Rohde_Schwarz_FSL3_Technical
---

# Rohde Schwarz FSL3

## About

The Rohde Schwarz FSL3 is a signal and spectrum analyzer. This connector is a virtual connector that owns the device connection in C# using the Rohde & Schwarz RsInstrument (VISA) library, issuing SCPI commands to expose the device identity, current measurement settings, and live trace data in DataMiner.

> [!NOTE]
> This connector is a single-element virtual/SCPI (VISA) connector. It does not use SNMP and does not export child elements (DVEs).

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection. The device connection is established from C# via the RsInstrument (VISA) library and is configured through the following parameters on the **General** page of the element:

- **Device IP Address**: The IP address/host of the device.
- **Device Port**: The IP port of the device (used for the Raw Socket connection type, by default *5025*).
- **Connection Type**: The VISA connection type used to reach the device. The following options are supported:
  - **VXI-11** (*0*)
  - **Raw Socket** (*1*, default, port *5025*)
  - **HiSLIP** (*2*)

> [!NOTE]
> Minimum required DataMiner version: **10.4.0.0 - 14003**.

## How to Use

On the **General** page, you can find device information such as the Manufacturer, Model, Serial Number, and Firmware Version, together with the current measurement settings:

- **Frequency**: center, span, start, and stop frequency.
- **Amplitude**: reference level, reference scale, amplitude units, and input attenuation (including AUTO).
- **Bandwidth**: resolution bandwidth (RBW) and video bandwidth (VBW), each with an AUTO mode.
- **Sweep**: sweep time (including AUTO), sweep mode (Single or Continuous), and a timeout safeguard.
- **Detection & scale**: detection mode and scale type.

You can enter new values for these settings and apply them to the device. The connector reads back the applied values on the next poll.

The page also provides two actions:

- **Preset**: Restores the instrument's default settings (`*RST`). This action is confirmation-guarded.
- **DMS Spectrum Measurements**: A toggle that enables or disables trace monitoring. When set to *Inhibited*, no measurements are initiated from the DataMiner Agent and the analyzer is put in automatic sweep.

The connector's spectrum analyzer component shows the live trace data captured from the device: the primary trace (an IEEE-754 float block returned by the instrument) is decoded into a level series and surfaced through the **DMSSpectrumMeasurements** spectrum measurement for trending and alarming. A zero-span, time-adjusted rolling trace acquisition can also be started on demand. For more information on how to work with spectrum analyzer elements, refer to [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).