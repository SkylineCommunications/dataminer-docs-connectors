---
uid: Connector_help_Rohde_Schwarz_FSL3_Technical
description: "Configure the Rohde Schwarz FSL3 connector in DataMiner: VISA and GPIB gateway connections, RF frequency translation, setting limits, and migration."
---

# Rohde Schwarz FSL3

## About

The **Rohde Schwarz FSL3** connector monitors and controls the R&S FSL3 spectrum analyzer via SCPI commands. It shows the traces of the analyzer in the DataMiner Spectrum Analysis module, lets you change the analyzer settings, and monitors the identity and health of the analyzer.

The connector does not export DVE child elements.

## Configuration

The information below applies to version 2.0.0.2 and higher. Versions 2.0.0.x connect to the analyzer through VISA and require DataMiner 10.4.0.0 - 14003 or higher. Versions 1.1.0.x use a serial connection. To move an element from 1.1.0.x, see [Migrating from 1.1.0.x to 2.0.0.x](#migrating-from-110x-to-200x).

### Connections

#### Virtual Connection

This connector uses a virtual connection. You do not need to configure any connection settings when you create the element. The connector opens the connection to the analyzer itself, with the settings on the **General** page.

A VISA library (R&S VISA or NI-VISA) must be installed on every DataMiner Agent that hosts an element of this connector. VISA is not included in the connector package. Without it, the connection fails. For a LAN/GPIB gateway, the VISA library must also be able to reach the gateway, e.g., with the Keysight IO Libraries.

### Initialization

After you have created the element, configure the connection on the **General** page:

1. In the **IP Address** box, enter the IP address of the analyzer. For GPIB via LAN Gateway, enter the IP address of the gateway instead.
1. In the **Connection Type** list, select the connection type:

   - **VXI-11** (default): For an analyzer on the LAN. This is the LAN protocol documented for the R&S FSL.
   - **GPIB via LAN Gateway**: For an analyzer with option FSL-B10 on a GPIB bus behind a LAN/GPIB gateway, e.g., a Keysight E5810A.
   - **Raw Socket** and **HiSLIP**: Not supported. See [Notes](#notes).

1. For GPIB via LAN Gateway, set **GPIB Address** to the GPIB address of the analyzer (0 to 30, default *20*).

   The connector will connect to the analyzer and fill in **Manufacturer**, **Model**, **Serial Number**, **Firmware Version**, and **Installed Options**.

> [!IMPORTANT]
> From version 2.0.0.2 onwards, the default connection type is *VXI-11*. An existing element that used Raw Socket without explicitly selecting a connection type switches to VXI-11 after the upgrade. Check the **Connection Type** of existing elements after the upgrade.

## How to Use

### Spectrum Analysis

To view traces and change the analyzer settings, open the element in the Spectrum Analysis module. The connector supports the standard spectrum analyzer features, such as spectrum presets, measurement points, and spectrum scripts. For more information, see [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

The measurement settings (frequencies, span, reference level, scale, attenuation, RBW, VBW, sweep time, sweep points, detection mode, and scale type) are not shown on the **General** page. You change them in the Spectrum Analysis module.

The attenuation, RBW, VBW, and sweep time can be set to *Auto*. The Spectrum Analysis module then shows the value selected by the analyzer.

The detection mode is applied as soon as you set it. You can select *Auto* or one of the seven detectors of the analyzer. The connector never changes the detector by itself. After a preset, the analyzer uses *Auto Peak*.

The RBW values 10 Hz, 30 Hz, and 100 Hz need option FSL-B7. The connector shows these values when the analyzer uses them, but you cannot select them.

### General Page

The **General** page contains the connection settings and the device identity, as well as these parameters:

- **Display Status**: Switches the analyzer display on or off during a measurement.
- **DMS Spectrum Measurements**: When set to *Inhibited*, DataMiner no longer starts any spectrum measurements on the analyzer, and the analyzer is set to continuous sweep. By default, *Inhibited* raises a warning alarm.
- **Sweep Mode**: *Single* or *Continuous*. The connector keeps the analyzer in the sweep mode you set. If the sweep mode is changed on the analyzer itself, the connector restores it at the next poll.
- **Zero Span Start Sweep**: Sets the span to 0 and starts a zero span acquisition at the center frequency. If the frequency setting is rejected, the sweep does not start.
- **Preset**: Resets the analyzer to its default settings and reads back all settings. You need to confirm this action.
- **LO Offset** and **LO Side**: Translate between RF and the frequencies of the analyzer. See [Working with RF frequencies](#working-with-rf-frequencies).
- **Reference Source**: *Internal* or *External* frequency reference.
- **IF Overload**: Indicates that the IF stage of the analyzer is overloaded. The measured levels are then not reliable. To solve this, increase the attenuation or the reference level, or reduce the input signal.
- **External Reference Status**: Indicates whether the external reference signal is missing or unlocked. This is only relevant when **Reference Source** is set to *External*.
- **Last Rejected Setting**: The last setting that was not applied, with the date and time (local time of the DataMiner Agent) and the reason. This covers values outside the range of the analyzer and values the analyzer refused. The parameter is empty until a setting is rejected.

The connector checks the connection every 10 seconds. **IF Overload** and **External Reference Status** are read with each check. The identification, the installed options, and the sweep mode are read every 5 minutes.

**IF Overload** and **External Reference Status** are monitored and trended. By default, *Overload* and *Missing or Unlocked* raise a major alarm.

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

### Setting Limits

The frequency range depends on the model that the analyzer reports in the **Model** parameter: 9 kHz to 3 GHz for an FSL3, and 9 kHz to 6 GHz for an FSL6. Any other model, or a model that is not known yet, gets the FSL3 range, and an unsupported model is logged. The model is read every 5 minutes, after a preset, and after a change of the connection settings.

Before the connector sends any frequency to the analyzer, it converts the center, start, and stop frequency and checks them against this range. When you set a center frequency and span together, without a start and stop frequency, the edges of the span are checked too. These edges can go down to 0 Hz. A negative RF frequency is always rejected.

If one of these values is out of range, the whole frequency setting is rejected and no frequency is sent to the analyzer. The other settings are still applied. The reason is shown in **Last Rejected Setting**, and the element log shows the RF value, the LO Offset, the LO Side, and the device value. The check also applies when **LO Offset** is 0.

With an LO, the valid RF range moves with the LO:

- **Low Side**: from 9 kHz + LO up to the maximum frequency + LO. For example, an FSL3 with an LO of 9750 MHz accepts 9750.009 MHz to 12750 MHz.
- **High Side**: from LO - maximum frequency up to LO - 9 kHz.

The connector also checks these settings against the FSL3 data sheet before it sends them:

- **Reference level**: -80 dBm to +20 dBm.
- **Input attenuation**: *Auto*, or 0 dB to 50 dB in steps of 5 dB.
- **Sweep points**: 101 to 32001.

A value outside these ranges is rejected and shown in **Last Rejected Setting**. The other settings are limited by the ranges of the parameters.

### Migrating from 1.1.0.x to 2.0.0.x

Range 2.0.0.x uses a virtual connection instead of a serial connection, and several parameter IDs have changed. For example, parameter ID 10 now contains the IP address, the **Preset** button moved from parameter ID 10 to 70, and the **Display Update** parameter was removed.

To migrate an element:

1. Install a VISA library on every DataMiner Agent that hosts an element.
1. Edit the element, and select a 2.0.0.x version, or create the element again.
1. On the **General** page, configure the connection as described under [Initialization](#initialization).
1. Update the alarm templates, trend templates, automation scripts, and spectrum presets that refer to parameter IDs that have changed.

## Notes

- **Raw Socket** is not supported. After a timeout, for example during a long sweep, the analyzer can stop answering on its socket port until you press *LOCAL* on the front panel or restart the analyzer. VXI-11 recovers by itself. **HiSLIP** is not documented for the R&S FSL. Both options are only kept for compatibility with existing elements.
- After an element restart, the center, start, and stop frequency can be empty until the next poll or until you apply new settings.
- The R&S FSL18 has its own connector, with the FSL18 limits.
- We recommend DataMiner 10.5.0 CU21, 10.6.0 CU9, 10.6.12, or later, with the matching DataMiner Cube version. These versions contain several fixes in the Spectrum Analysis module for spectrum presets and shared mode. See [DataMiner Cube 10.6.12](https://docs.dataminer.services/release-notes/Cube/Cube_Feature_Release_10.6/Cube_10.6.12.html), RN 46514, 46516, 46555, 46585, and 46668.