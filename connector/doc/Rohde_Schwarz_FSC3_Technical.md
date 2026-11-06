---
uid: Connector_help_Rohde_Schwarz_FSC3_Technical
description: "Configure the Rohde Schwarz FSC3 connector in DataMiner: VISA connection, RF frequency translation, device limits, and spectrum analysis."
---

# Rohde Schwarz FSC3

## About

The **Rohde Schwarz FSC3** connector monitors and controls the R&S FSC3 spectrum analyzer (9 kHz to 3 GHz) via SCPI commands over VISA. It shows the traces of the analyzer in the DataMiner Spectrum Analysis module, lets you change the analyzer settings, and monitors the identity and health of the analyzer.

The connector is intended for the R&S FSC3 (order numbers 1314.3006.03 and 1314.3006.13). It does not export DVE child elements.

## Configuration

The current version of the connector requires DataMiner 10.4.0.0 - 14003 or higher.

### Connections

#### Virtual Connection

This connector uses a virtual connection. You do not need to configure any connection settings when you create the element. The connector opens the connection to the analyzer itself, with the settings on the **General** page.

A VISA library must be installed on every DataMiner Agent that hosts an element of this connector: R&S VISA 5.12 or higher, or NI-VISA 18 or higher. VISA is not included in the connector package. Without it, the connection fails.

### Initialization

After you have created the element, configure the connection on the **General** page:

1. In the **IP Address** box, enter the IP address of the analyzer.
1. In the **Connection Type** list, select the connection type:

   - **VXI-11**
   - **Raw Socket** (default)
   - **HiSLIP**

1. If you use Raw Socket, set **Port** to the port of the analyzer, or select *Auto* to use port *5025*. The port is not used for the other connection types.

   The connector will connect to the analyzer and fill in **Manufacturer**, **Model**, **Serial Number**, **Firmware Version**, and **Installed Options**.

Remote control of the R&S FSC3 needs the option R&S FSC-K40. You can check this in **Installed Options**.

## How to Use

### Spectrum Analysis

To view traces and change the analyzer settings, open the element in the Spectrum Analysis module. The connector supports the standard spectrum analyzer features, such as spectrum presets, measurement points, and spectrum scripts. For more information, see [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

The measurement settings (frequencies, span, reference level, scale, attenuation, RBW, VBW, sweep time, and sweep points) are not shown on the **General** page. You change them in the Spectrum Analysis module.

### General Page

The **General** page contains the connection settings and the device identity, as well as these parameters:

- **Display Status**: Switches the analyzer display on or off during a single sweep measurement.
- **Display Update**: Switches the analyzer display on or off in remote control mode. The analyzer performs best when its display is off.
- **Sweep Mode**: *Single* or *Continuous*. The connector only changes the sweep mode when you set it. The poll only reads it.
- **LO Offset** and **LO Side**: Translate between RF and the frequencies of the analyzer. See [Working with RF frequencies](#working-with-rf-frequencies).
- **Detector**: The detector the analyzer uses. Select *Auto* to let the analyzer choose. The connector never changes the detector by itself.
- **Reference Source**: *Internal* or *External*. When you select *External*, BNC connector 1 of the analyzer is switched to reference input, so you can no longer use it as a trigger input.
- **IF Overload**: Indicates that the IF stage of the analyzer is overloaded. The measured levels are then not reliable. To solve this, increase the attenuation or the reference level, or reduce the input signal.
- **External Reference Status**: Indicates whether the external reference signal is missing or unlocked. This is only relevant when **Reference Source** is set to *External*.
- **Preset**: Resets the analyzer to its default settings and reads back all settings. You need to confirm this action.
- **Zero Span Sweep**: Sets the span to 0 and starts a zero span acquisition at the center frequency.

The connector checks the connection every 10 seconds. On an R&S FSC, **IF Overload** and **External Reference Status** are read with each check. The identification and the installed options are read every 5 minutes.

**IF Overload** and **External Reference Status** are monitored and trended, but they have no default alarm thresholds. Configure them in the alarm template if you want alarms.

### Working with RF Frequencies

When the analyzer measures the output of an LNB or downconverter, the analyzer works in L-band or IF, while operators work in RF. With **LO Offset** and **LO Side**, the connector does the conversion for you:

- You enter and see the center, start, and stop frequency in RF.
- The connector converts these frequencies before it sends them to the analyzer, and converts the values it reads back to RF.

The conversion depends on the LO side:

- **Low Side**: device frequency = RF - LO. For example, with an LO of 9750 MHz, an RF frequency of 10730 MHz is tuned to 980 MHz on the analyzer.
- **High Side**: device frequency = LO - RF. The spectrum is inverted, so the connector swaps the start and stop frequency and reverses the trace. In zero span, only the center frequency is converted. For example, with an LO of 5150 MHz, an RF frequency of 3900 MHz is tuned to 1250 MHz on the analyzer.

Only the center, start, and stop frequency are converted. The span, RBW, VBW, reference level, attenuation, and sweep settings are not converted. An **LO Offset** of 0 means no conversion.

To configure the conversion:

1. Make sure no measurement point, script, or display offset already converts the frequencies. Otherwise, the conversion is applied twice.
1. On the **General** page, set **LO Side** to the side of the downconverter LO: *Low Side* or *High Side*.
1. Set **LO Offset** to the LO frequency in MHz (0 to 50000 MHz, with up to 3 decimals).

   The connector will show the center, start, and stop frequency in RF. Nothing is sent to the analyzer when you change the LO settings.

1. Save again any spectrum presets that contain L-band frequencies, so that they contain RF frequencies.

A negative or out-of-range **LO Offset** is rejected and logged. The previous value is kept.

### Frequency Limits

The R&S FSC3 can be tuned from **9 kHz to 3 GHz**. Before the connector sends any frequency to the analyzer, it converts the center, start, and stop frequency and checks them against this range. When you set a center frequency and span together, without a start and stop frequency, the edges of the span are checked too. These edges can go down to 0 Hz.

If one of these values is out of range, the whole frequency setting is rejected and nothing is sent to the analyzer. The element log shows the RF value, the LO Offset, the LO Side, and the device value. The check also applies when **LO Offset** is 0.

With an LO, the valid RF range moves with the LO:

- **Low Side**: from 9 kHz + LO up to 3 GHz + LO. For example, with an LO of 9750 MHz, from 9750.009 MHz to 12750 MHz.
- **High Side**: from LO - 3 GHz up to LO - 9 kHz.

The other settings are limited by the ranges of the parameters. Some of these ranges are wider than the FSC3 data sheet, because other R&S analyzer models can also be used with this connector.

## Notes

- **LO Offset**, **LO Side**, and the frequency range check are available from version 1.2.0.3 onwards. **Detector**, **Installed Options**, **Reference Source**, **IF Overload**, and **External Reference Status** are available from version 1.2.0.4 onwards.
- On an R&S FSC, the connector shows the model and the serial number as separate values, and sets the level unit to dBm.
- After an element restart, the center, start, and stop frequency can be empty until the next poll or until you apply new settings.
- In Continuous sweep mode, the **Sweep Mode** parameter is in alarm, and when **Display Update** is *Off*, that parameter is in alarm too. Adjust the alarm template if these settings are normal in your setup.
