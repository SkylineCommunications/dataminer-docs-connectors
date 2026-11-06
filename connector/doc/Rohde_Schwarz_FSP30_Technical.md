---
uid: Connector_help_Rohde_Schwarz_FSP30_Technical
description: "Configure the Rohde Schwarz FSP30 connector in DataMiner: GPIB or RS-232 connection, Spectrum Analysis usage, and LO frequency translation."
---

# Rohde Schwarz FSP30

## About

The Rohde Schwarz FSP30 is a spectrum analyzer with a frequency range of 9 kHz to 30 GHz. This connector uses a serial connection to send SCPI commands to the analyzer. It reads the identification, the measurement settings, and the trace, and makes them available in the DataMiner Spectrum Analysis module.

The connector does not export child elements (DVEs).

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection (**Device Connection**). The analyzer has no raw SCPI socket. It can only be reached over GPIB or RS-232. Connecting to the analyzer by IP address, through a LAN/GPIB gateway or the LAN option FSP-B16, is not supported by this connector.

Choose one of the following paths during element creation.

**GPIB (recommended)**: The DataMiner Agent needs a GPIB interface, e.g., a GPIB card with its driver, or a LAN/GPIB gateway that is configured in the VISA configuration tool as a remote GPIB interface.

- **Type of port**: GPIB.
- **Bus address**: The GPIB address of the analyzer (range *0* to *32*). You can find the address on the analyzer under **SETUP** > **GENERAL SETUP** > **GPIB ADDRESS**.

**RS-232**: A null-modem cable connects the analyzer COM port to a COM port of the DataMiner Agent.

- **Type of port**: Serial, with the COM port of the DataMiner Agent.
- **Baud rate**: The baud rate configured on the analyzer (default: *9600*). The analyzer supports 110 to 19200 baud.
- **Data bits**: *8*.
- **Parity**: *None*.
- **Stop bits**: *1*.
- **Flow control**: *No*.

Check the COM port settings on the analyzer under **SETUP** > **GENERAL SETUP** > **COM PORT**.

> [!WARNING]
> According to the analyzer documentation, the FSP cannot send block data over RS-232. Settings and read-back work, but the trace may stay empty. If the trace does work, it is slow: at 9600 baud, a trace of 8001 points takes about 33 seconds. Use GPIB to get traces.

### Initialization

No extra configuration is needed. After startup, the connector restores the saved sweep points and display status on the analyzer, and reads the identification and the current settings.

## How to Use

### Spectrum Analyzer

The element is a spectrum analyzer element. Open it in the DataMiner Spectrum Analysis module to see the live trace and to change the measurement settings: center, start, and stop frequency, span, reference level, reference scale, resolution bandwidth (RBW), video bandwidth (VBW), sweep time, input attenuation, detector, scale type, and sweep points. For more information, refer to [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

Keep the following in mind:

- RBW, VBW, sweep time, and input attenuation have an automatic mode. In automatic mode, the analyzer selects the value, and the connector shows the value that is in use.
- The input attenuation is set in 10 dB steps by the analyzer (0 to 70 dB). Other values are rounded by the analyzer.
- The analyzer is only switched to single sweep when a trace is requested. Between requests, the sweep mode set on the front panel is kept.
- The sweep points value is saved and sent to the analyzer again after a restart of the element.

### General Page

This page shows the identification of the analyzer (**Manufacturer**, **Model**, **Serial Number**, and **Firmware Version**) and contains the following settings:

- **Display Status**: Sets whether the analyzer screen is updated during a single sweep. Switching it off can increase the measurement rate.
- **LO Offset** and **LO Side**: Configure the RF frequency translation. See [Frequency translation with LO Offset and LO Side](#frequency-translation-with-lo-offset-and-lo-side).
- **DMS Spectrum Measurements**: Set this to *Inhibited* to stop all DataMiner measurements on the analyzer, e.g., during maintenance. While measurements are inhibited, DataMiner sends no settings and requests no traces, and the analyzer is set to continuous sweep. Set it back to *Allowed* to resume.

### Frequency Translation with LO Offset and LO Side

Use these settings when a frequency converter, e.g., an LNB or a down converter, is placed in front of the analyzer. The analyzer then measures the converted frequency (e.g., L-band or IF), but you see and enter RF frequencies.

To configure the translation:

1. On the **General** page, set **LO Offset** to the LO frequency of the converter, in MHz.

   The range is 0 to 50000 MHz. A value outside this range is ignored and logged in the element log.

1. Set **LO Side** to match the converter:

   - **Low Side** (default): analyzer frequency = RF - LO.
   - **High Side**: analyzer frequency = LO - RF. Because the spectrum is inverted, the connector swaps the start and stop frequencies and reverses the trace, so that the trace is still shown with increasing RF frequency. In zero span, the trace is not reversed.

1. In the Spectrum Analysis module, set the center, start, or stop frequency in RF.

   The connector will convert the values to analyzer frequencies before it sends them.

Keep the following in mind:

- Only the center, start, and stop frequency are translated. The span, bandwidths, levels, and sweep settings are not changed.
- An **LO Offset** of *0* means no translation. The frequencies are the analyzer input frequencies, as in older versions of the connector.
- Changing **LO Offset** or **LO Side** sends nothing to the analyzer. The connector only recalculates the frequencies it shows. To measure the same RF frequency after a change, set the frequency again.
- If a script, preset, or measurement point already adds or subtracts the LO, keep **LO Offset** at *0*. Otherwise, the LO is applied twice.

### Frequency Limits

The analyzer accepts frequencies from 9 kHz to 30 GHz. The RF frequency parameters accept values up to 80 GHz, so that RF values above the analyzer range can be shown and entered when an LO is set. The span is limited to 0 to 30 GHz.

When **LO Offset** is not 0, the connector checks the translated center, start, and stop frequency before it sends them. If a translated value is outside 9 kHz to 30 GHz, the connector does not send the frequency settings and logs the reason in the element log. The other settings of the same change are still sent.

When **LO Offset** is 0, the connector does not check the frequencies. The analyzer handles out-of-range values itself, and any error it reports is logged (see below).

### Device Errors

After every settings change, the connector reads the error queue of the analyzer (`SYST:ERR?`). If the analyzer reports an error, it is logged as an error in the element log, e.g., `Device error after Set Data: <code>, <message>`. One error is read per settings change.

### Using the Connector from Automation Scripts

Scripts use the same parameters as the Spectrum Analysis module:

1. Fill in the write parameters of the settings to change (e.g., center frequency, span, RBW).
1. Set **Flag for set command** (parameter 64118) to *1*.

   The connector will send all filled-in values in one command, read them back, and read the error queue.

1. To request a trace, set **Settings Done** (parameter 64116) to *1*.

   The connector will set the analyzer to single sweep, run one sweep, and update the trace. Setting **Settings Done** to *0* clears the write parameters.

With an LO configured, write RF values to the center, start, and stop frequency.

## Notes

- Range 3.1.0.x requires DataMiner 10.4.0.0 (build 14003) or later. Elements on range 3.0.0.x are not moved to 3.1.0.x automatically: upgrade DataMiner first, and then change the element to range 3.1.0.x. All parameter IDs and discrete values are kept.
- The connector supports a single trace. It has no preset, reference source, markers, or sweep mode setting.
- The reference level is shown in dBm. When the analyzer uses dBmV, dBµV, V, or W, the connector converts the value to dBm. Other level units are not converted.
- DataMiner 10.6.0 CU9, 10.6.12, or later is recommended, as these versions include significant Spectrum Analysis fixes.
- Other analyzers of the FSP family (e.g., FSP3, FSP7, FSP13, and FSP40) use the same commands, but have different frequency and attenuation ranges. They have not been qualified with this connector.
