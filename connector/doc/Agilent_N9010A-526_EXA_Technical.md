---
uid: Connector_help_Agilent_N9010A-526_EXA_Technical
description: "Configure the Agilent N9010A-526 EXA connector in DataMiner: VISA connection, LO Offset frequency translation, device limits, and measurement controls."
---

# Agilent N9010A-526 EXA

## About

The Agilent N9010A-526 EXA connector monitors and controls an Agilent (now Keysight) N9010A EXA signal analyzer with Option 526. The connector sends SCPI commands to the analyzer over VISA, using the RsInstrument library. It shows the instrument identity and the main device settings on the **General** page, and the live trace on the **Spectrum Analyzer** page.

With Option 526, the analyzer covers **10 Hz to 26.5 GHz** (DC coupled).

## Configuration

This connector requires DataMiner **10.4.0.0 - 14003** or higher.

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation. The connector opens the VISA session to the analyzer itself, based on the settings on the **General** page. The connector has communicated through VISA since version 1.1.0.1. Older versions used a serial connection.

> [!NOTE]
> A VISA library (e.g., R&S VISA or NI-VISA) must be installed on every DataMiner Agent that hosts an element using this connector. This applies to all connection types. VISA is not included in the connector package. Without it, the connection fails.

### Initialization

After you have created the element, configure the connection on the **General** page:

1. Set **IP Address** to the IP address or hostname of the analyzer.

1. Set **RS Connection Type** to *VXI-11*, *Raw Socket* (default), or *HiSLIP*.

1. If you use Raw Socket, check **Port**.

   When **Port** is set to *Auto*, the connector uses port *5025*. The port is not used for VXI-11 and HiSLIP.

When the connection is established, the identification parameters on the **General** page will be filled in.

Keep the following in mind when you choose a connection type:

- On the analyzer, the SCPI socket, HiSLIP, and VXI-11 servers can each be switched off (**System** > **I/O Config** > **SCPI LAN**). The server for the selected connection type must be switched on.
- VXI-11 supports only one controlling session. If another application also controls the analyzer, use HiSLIP, which supports multiple sessions. HiSLIP requires analyzer firmware A.11.00 or later.
- Port 5025 is the usual SCPI socket port on Keysight analyzers, but it has not been confirmed for this model. If the analyzer uses another port, enter that port in **Port**.

## How to Use

### Spectrum Analyzer Page

This page shows the live trace in the DataMiner spectrum analyzer component. You also change the measurement settings here: center, start, and stop frequency, span, reference level, scale, resolution bandwidth (RBW), video bandwidth (VBW), sweep time, sweep points, and input attenuation.

RBW, VBW, sweep time, and input attenuation can be set to *Auto*. In that case, the analyzer chooses the value itself. Automation scripts select *Auto* by writing the value -1.

For more information on how to use this page, refer to [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

> [!TIP]
> A narrow RBW over a wide span makes the sweep much longer. If a trace takes too long, use a wider RBW, a smaller span, or set RBW to *Auto*.

### General Page

This page contains the connection settings, the instrument identification, and the following settings and actions:

- **Manufacturer**, **Model**, **Serial Number**, **Firmware Version**, and **Installed Options**: The identification of the analyzer. **Installed Options** shows the options reported by the analyzer, e.g., *526* for the 26.5 GHz frequency range. These values are refreshed every 5 minutes, after a reconnection, and after a preset.
- **Sweep Mode**: Switches between *Single* and *Continuous* sweep. The connector only sends the sweep mode to the analyzer when you change it. By default, *Continuous* raises a critical alarm.
- **Zero Span Sweep**: Sets the span to 0 and starts a zero-span acquisition at the current center frequency. The connector asks for confirmation first.
- **Preset**: Stops the current sweep, restores the default settings of the analyzer, and then reads back all settings. The connector asks for confirmation first.
- **Detector**: Shows the detector of trace 1 that the analyzer is currently using. Select a detector to change it, or select *Auto* to let the analyzer choose. *Quasi Peak*, *EMI Average*, and *RMS Average* require the EMC option on the analyzer. The connector never changes the detector by itself, not even after a preset.
- **LO Offset** and **LO Side**: See [Working with RF frequencies behind a downconverter](#working-with-rf-frequencies-behind-a-downconverter).

### Working with RF Frequencies Behind a Downconverter

When the analyzer measures the L-band or IF output of a downconverter (e.g., an LNB), the connector can translate frequencies for you. You see and enter RF frequencies, and the connector tunes the analyzer to the matching L-band or IF frequency. This feature is available from version 1.2.0.4 onwards.

To configure this:

1. On the **General** page, set **LO Side**:

   - *Low Side* if the local oscillator (LO) of the downconverter is below the RF frequency, e.g., a Ku-band LNB with an LO of 9750 MHz. The analyzer is tuned to RF − LO.
   - *High Side* if the LO is above the RF frequency, e.g., a C-band LNB with an LO of 5150 MHz. The analyzer is tuned to LO − RF.

1. Set **LO Offset** to the LO frequency in MHz, e.g., *9750*.

   You can enter 0 to 50000 MHz, with up to 3 decimals. Negative values are not accepted. Use **LO Side** for the direction.

   The center, start, and stop frequencies will be shown as RF values. Nothing is sent to the analyzer when you change these settings.

To stop translating frequencies, set **LO Offset** to *0*. With LO Offset 0, **LO Side** is ignored and the connector works with the frequencies of the analyzer itself. This is the default.

Example: with **LO Offset** *9750* and **LO Side** *Low Side*, an RF center frequency of 10730 MHz tunes the analyzer to 980 MHz.

Keep the following in mind:

- Only the center, start, and stop frequencies are translated. Span, bandwidths, reference level, scale, attenuation, sweep time, and sweep points are not changed.
- With *High Side*, the spectrum is inverted. The connector swaps the start and stop frequencies and reverses the trace, so the trace is shown correctly on the RF axis. In zero span, the trace is not reversed.
- LO Offset and LO Side are saved and remain set after an element or DataMiner restart.
- Automation scripts can set LO Offset and LO Side through the write parameters 81 and 83.

> [!WARNING]
> If a solution already translates frequencies for this element, e.g., an Automation script that subtracts the LO or a measurement point with a frequency offset, setting LO Offset applies the LO twice. Remove that translation before you set LO Offset. Spectrum presets saved with L-band frequencies must be saved again with RF frequencies.

### Device Frequency Limits

Before it sends frequency settings to the analyzer, the connector checks the device frequency, i.e., the value after LO translation, against the range of the N9010A with Option 526: **10 Hz to 26.5 GHz**. This check also applies when LO Offset is 0. Versions before 1.2.0.4 did not check the frequency range.

The center, start, and stop frequencies are checked. When a center frequency and a span are applied together, the edges of the span are checked too.

If a value is out of range:

- The connector rejects all frequency settings of that change and does not send them to the analyzer, so the analyzer keeps its current frequencies.
- The rejection is logged in the element log, with the RF value, the LO settings, and the calculated device value.
- The other settings of the same change are still applied.
- **Zero Span Sweep** does not start.

For example, with **LO Offset** *9750* and **LO Side** *Low Side*, you can enter RF frequencies from about 9750 MHz up to 36250 MHz.

## Notes

- The frequency read parameters are not saved. After a restart, they stay empty until settings are applied, e.g., when the Spectrum Analysis module sends its settings.
- For compatibility with existing scripts and presets, some ranges are wider than the data sheet: reference level up to +30 dBm (data sheet: +23 dBm), scale up to 100 dB/div (data sheet: 20 dB/div), and RBW and VBW 10 MHz. The analyzer limits these values itself, and the connector shows the value the analyzer applied.
- The connector does not enforce the attenuation step size (10 dB, or 2 dB with Option FSA).
- When the analyzer input is AC coupled, its lower frequency limit is 10 MHz. The connector does not know the coupling and checks against the DC-coupled range of 10 Hz.
- In versions before 1.2.0.4, values could be read incorrectly on DataMiner Agents that use a comma as decimal separator, and the periodic poll could reset the sweep mode on the analyzer. Upgrade to 1.2.0.4 or later to avoid this.
