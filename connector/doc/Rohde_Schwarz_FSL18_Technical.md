---
uid: Connector_help_Rohde_Schwarz_FSL18_Technical
description: "Configure the Rohde Schwarz FSL18 connector in DataMiner: VISA connection, RF frequency translation, device limits, and spectrum analysis."
---

# Rohde Schwarz FSL18

## About

The **Rohde Schwarz FSL18** connector monitors and controls the R&S FSL18 spectrum analyzer (9 kHz to 18 GHz) via SCPI commands over VISA. It shows the traces of the analyzer in the DataMiner Spectrum Analysis module, lets you change the analyzer settings, and monitors the identity and health of the analyzer.

The connector has the same features and parameter IDs as version 2.0.0.x of the [Rohde Schwarz FSL3](xref:Connector_help_Rohde_Schwarz_FSL3) connector, so spectrum presets and Visual Overview pages made for that connector can be reused. The ranges, limits, and connection types are specific to the FSL18.

The connector is intended for the R&S FSL18 (order numbers 1300.2502.18, and 1300.2502.28 with tracking generator). It does not check the model of the analyzer, and it applies the FSL18 limits to any analyzer it is connected to. For the R&S FSL3 and FSL6, use the [Rohde Schwarz FSL3](xref:Connector_help_Rohde_Schwarz_FSL3) connector. The connector does not export DVE child elements.

## Configuration

This connector requires DataMiner 10.4.0.0 - 14003 or higher.

### Connections

#### Virtual Connection

This connector uses a virtual connection. You do not need to configure any connection settings when you create the element. The connector opens the connection to the analyzer itself, with the settings on the **General** page.

A VISA library must be installed on every DataMiner Agent that hosts an element of this connector: R&S VISA 5.12 or higher, or NI-VISA 18 or higher. VISA is not included in the connector package. Without it, the connection fails. For a LAN/GPIB gateway, the VISA library must also be able to reach the gateway, e.g., with the Keysight IO Libraries.

### Initialization

After you have created the element, configure the connection on the **General** page:

1. In the **IP Address** box, enter the IP address of the analyzer. For GPIB via LAN Gateway, enter the IP address of the gateway instead.
1. In the **Connection Type** list, select the connection type:

   - **VXI-11** (default): The LAN protocol documented for the R&S FSL.
   - **Raw Socket**: Uses the port in the **Port** box. Select *Auto* to use port *5025*. Raw Socket is not documented for the R&S FSL.
   - **GPIB via LAN Gateway**: For an analyzer with option FSL-B10 on a GPIB bus behind a LAN/GPIB gateway, e.g., a Keysight E5810A.

1. For GPIB via LAN Gateway, set **GPIB Address** to the GPIB address of the analyzer (0 to 30, default *20*).

   The connector will connect to the analyzer and fill in **Manufacturer**, **Model**, **Serial Number**, **Firmware Version**, and **Installed Options**.

HiSLIP is not available in this connector.

## How to Use

### Spectrum Analysis

To view traces and change the analyzer settings, open the element in the Spectrum Analysis module. The connector supports the standard spectrum analyzer features, such as spectrum presets, measurement points, and spectrum scripts. For more information, see [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

The measurement settings (frequencies, span, reference level, scale, attenuation, RBW, VBW, sweep time, sweep points, detection mode, and scale type) are not shown on the **General** page. You change them in the Spectrum Analysis module.

The detection mode is applied as soon as you set it. You can select *Auto* or one of the seven detectors of the analyzer. The connector never changes the detector by itself.

The RBW values 10 Hz, 30 Hz, and 100 Hz need option FSL-B7. The connector shows these values when the analyzer uses them, but you cannot select them.

### General Page

The **General** page contains the connection settings and the device identity, as well as these parameters:

- **Display Status**: Switches the analyzer display on or off during a measurement.
- **DMS Spectrum Measurements**: When set to *Inhibited*, DataMiner no longer starts any spectrum measurements on the analyzer, and the analyzer is set to continuous sweep.
- **Sweep Mode**: *Single* or *Continuous*. The connector only changes the sweep mode when you set it. The poll only reads it.
- **Zero Span Sweep**: Sets the span to 0 and starts a zero span acquisition at the center frequency. If the frequency setting is rejected, the sweep does not start.
- **Preset**: Resets the analyzer to its default settings and reads back all settings. You need to confirm this action.
- **LO Offset** and **LO Side**: Translate between RF and the frequencies of the analyzer. See [Working with RF frequencies](#working-with-rf-frequencies).
- **Reference Source**: *Internal* or *External* frequency reference.
- **IF Overload**: Indicates that the IF stage of the analyzer is overloaded. The measured levels are then not reliable. To solve this, increase the attenuation or the reference level, or reduce the input signal.
- **External Reference Status**: Indicates whether the external reference signal is missing or unlocked. This is only relevant when **Reference Source** is set to *External*.

The connector checks the connection every 10 seconds, and reads **IF Overload** and **External Reference Status** with each check. The identification and the installed options are read every 5 minutes.

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

### Device Limits

Before the connector sends a setting to the analyzer, it checks the setting against the limits of the R&S FSL18:

- **Center, start, and stop frequency**: 9 kHz to 18 GHz on the analyzer, after the LO conversion.
- **Span edges** (center ± span / 2): 0 Hz to 20 GHz. These are only checked when you set a center frequency and span together, without a start and stop frequency, or in zero span.
- **Input attenuation**: *Auto*, or 0 dB to 40 dB in steps of 5 dB.
- **Reference level**: -80 dBm to +20 dBm.
- **Sweep points**: a whole number from 101 to 32001.

If a frequency is out of range, the whole frequency setting is rejected and no frequency is sent to the analyzer. The element log shows the RF value, the LO Offset, the LO Side, and the device value. The check also applies when **LO Offset** is 0, and a negative RF frequency is always rejected.

If the attenuation, reference level, or number of sweep points is out of range, only that setting is rejected and logged. The value is never rounded or limited to the nearest valid value. The other settings are still applied.

These checks also apply to values that are set by scripts or from the Spectrum Analysis module.

With an LO, the valid RF range moves with the LO:

- **Low Side**: from 9 kHz + LO up to 18 GHz + LO. For example, with an LO of 9750 MHz, from 9750.009 MHz to 27750 MHz.
- **High Side**: from LO - 18 GHz up to LO - 9 kHz. For example, with an LO of 5150 MHz, any RF frequency from 0 MHz up to 5149.991 MHz.

The other settings are limited by the ranges of the parameters: span 0 to 20 GHz, scale 1 to 20 dB/div, sweep time 1 µs to 16000 s, RBW 300 Hz to 10 MHz, and VBW 1 Hz to 10 MHz. The analyzer itself enforces the minimum sweep time for a span greater than 0.

### Moving Elements from the Rohde Schwarz FSL3 Connector

The parameter IDs are the same as in version 2.0.0.x of the Rohde Schwarz FSL3 connector. When you move an FSL18 element from that connector to this connector, check the connection type:

- HiSLIP is not available. Select *VXI-11* instead.
- The default connection type is VXI-11 instead of Raw Socket. If the element relied on the Raw Socket default, select *Raw Socket* explicitly.

## Notes

- After an element restart, the center, start, and stop frequency can be empty until the next poll or until you apply new settings.
- Center, start, and stop frequencies above 18 GHz on the analyzer are rejected. The 18 GHz to 20 GHz overrange of the analyzer is not supported yet.
- Only the first trace is read. Trace modes, such as max hold, are not set by the connector.
