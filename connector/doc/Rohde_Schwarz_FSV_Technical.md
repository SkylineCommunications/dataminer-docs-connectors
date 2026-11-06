---
uid: Connector_help_Rohde_Schwarz_FSV_Technical
description: "Configure the Rohde Schwarz FSV connector in DataMiner: VISA connection, LO Offset frequency translation, per-model limits, and measurement controls."
---

# Rohde Schwarz FSV

## About

The Rohde Schwarz FSV connector monitors and controls an R&S FSV signal and spectrum analyzer. The connector sends SCPI commands to the analyzer over VISA, using the R&S RsInstrument library. It shows the instrument identity and the main device settings on the **General** page, and the live trace on the **Spectrum Analyzer** page.

One connector serves the whole FSV family. The connector uses the **Model** reported by the analyzer to select the frequency range: FSV3 (3 GHz), FSV4 (4 GHz), FSV7 (7 GHz), FSV13 (13.6 GHz), FSV30 (30 GHz), and FSV40 (40 GHz). An FSVA uses the range of the FSV with the same number.

## Configuration

This connector requires DataMiner **10.4.0.0 - 14003** or higher.

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation. The connector opens the VISA session to the analyzer itself, based on the settings on the **General** page. From version 1.0.0.4 onwards, the connector uses this virtual VISA connection instead of a serial connection.

> [!NOTE]
> A VISA library (e.g., R&S VISA or NI-VISA) must be installed on every DataMiner Agent that hosts an element using this connector. This applies to all connection types. VISA is not included in the connector package. Without it, the connection fails.

### Initialization

After you have created the element, configure the connection on the **General** page:

1. Set **IP Address** to the IP address or hostname of the analyzer.

1. Set **Connection Type** to *VXI-11*, *Raw Socket* (default), or *HiSLIP*.

1. If you use Raw Socket, check **Port**.

   When **Port** is set to *Auto*, the connector uses port *5025*. The port is not used for VXI-11 and HiSLIP.

1. When the element is connected, check that **Model** shows the expected FSV model.

   The model determines the frequency range that the connector allows. If the model is not recognized, the connector uses the widest family range of 10 Hz to 40 GHz.

> [!NOTE]
> The FSV documentation does not specify a port for raw SCPI socket connections, and port 5025 has not been confirmed on an FSV. If Raw Socket does not connect, use VXI-11 or HiSLIP, or enter the port that the analyzer reports for the `SYST:COMM:TCP:CONT?` query.

## How to Use

### Spectrum Analyzer Page

This page shows the live trace in the DataMiner spectrum analyzer component. You also change the measurement settings here: center, start, and stop frequency, span, reference level, scale, resolution bandwidth (RBW), video bandwidth (VBW), sweep time, sweep points, and input attenuation.

RBW, VBW, sweep time, and input attenuation can be set to *Auto*. In that case, the analyzer chooses the value itself. Automation scripts select *Auto* by writing the value -1.

For more information on how to use this page, refer to [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

### General Page

This page contains the connection settings, the instrument identification, and the following settings and actions:

- **Serial Number**, **Firmware Version**, **Manufacturer**, **Model**, and **Installed Options**: The identification of the analyzer. **Installed Options** shows the options reported by the analyzer, e.g., *K54* for the quasipeak detector. These values are refreshed every 5 minutes, after a reconnection, and after a preset.
- **Display Status**: Switches the analyzer display on or off during a single sweep measurement. By default, *Off* raises a critical alarm.
- **Display Update**: Switches the analyzer display on or off in remote control mode. The analyzer performs best with the display off. By default, *Off* raises a critical alarm.
- **Sweep Mode**: Switches between *Single* and *Continuous* sweep. The connector only sends the sweep mode to the analyzer when you change it. By default, *Continuous* raises a critical alarm.
- **Detector**: Shows the detector that the analyzer is currently using. Select a detector to change it, or select *Auto* to let the analyzer choose. *Quasipeak* requires option R&S FSV-K54. The connector never changes the detector by itself. After a preset, the analyzer uses its default detector.
- **LO Offset** and **LO Side**: See [Working with RF frequencies behind a downconverter](#working-with-rf-frequencies-behind-a-downconverter).
- **Preset**: Stops the current sweep, restores the default settings of the analyzer, and then reads back all settings. The connector asks for confirmation first.
- **Zero Span Sweep**: Sets the span to 0 and starts a zero-span acquisition at the current center frequency. The connector asks for confirmation first.

### Working with RF Frequencies Behind a Downconverter

When the analyzer measures the L-band or IF output of a downconverter (e.g., an LNB), the connector can translate frequencies for you. You see and enter RF frequencies, and the connector tunes the analyzer to the matching L-band or IF frequency. This feature is available from version 2.0.0.2 onwards. If the analyzer measures the RF signal directly, keep **LO Offset** at *0*.

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

Before it sends frequency settings to the analyzer, the connector checks the device frequency, i.e., the value after LO translation, against the range of the connected model: from **10 Hz** up to the maximum of the model (see [About](#about)). This check also applies when LO Offset is 0.

The center, start, and stop frequencies are checked. When a center frequency and a span are applied together, the edges of the span are checked too.

If a value is out of range:

- The connector rejects all frequency settings of that change and does not send them to the analyzer, so the analyzer keeps its current frequencies.
- The rejection is logged in the element log, with the RF value, the LO settings, the calculated device value, and the model range.
- The other settings of the same change are still applied.
- **Zero Span Sweep** does not start.

For example, on an FSV7 with **LO Offset** *9750* and **LO Side** *Low Side*, you can enter RF frequencies from about 9750 MHz up to 16750 MHz.

## Notes

- The frequency read parameters are not saved. After a restart, they stay empty until settings are applied, e.g., when the Spectrum Analysis module sends its settings.
- After a preset, the analyzer input is AC coupled, which raises its lower frequency limit (1 MHz on the FSV4 and FSV7, 10 MHz on the FSV13 and higher). The connector does not read the coupling and checks against the DC-coupled minimum of 10 Hz.
- The maximum input attenuation of 75 dB comes from the current FSV data sheet. It has not been confirmed yet on older FSV units and on FSVA units.
- In versions before 2.0.0.2, values could be read incorrectly on DataMiner Agents that use a comma as decimal separator, and the periodic poll could reset the sweep mode on the analyzer. Upgrade to 2.0.0.2 or later to avoid this.
