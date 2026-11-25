---
uid: Connector_help_Rohde_Schwarz_FSL18_Technical
description: "Configure the Rohde Schwarz FSL18 connector in DataMiner: VISA connections, RF frequency translation, setting limits, and troubleshooting."
---

# Rohde Schwarz FSL18

## About

The **Rohde Schwarz FSL18** connector monitors and controls the R&S FSL18 spectrum analyzer via SCPI commands. It shows the traces of the analyzer in the DataMiner Spectrum Analysis module, lets you change the analyzer settings, and monitors the identity and health of the analyzer.

The connector has been tested with firmware version 2.00 SP2 of the analyzer.

The connector does not export DVE child elements.

## Configuration

This connector requires DataMiner 10.4.0.0 - 14003 or higher.

### Connections

#### Virtual Connection

This connector uses a virtual connection. You do not need to configure any connection settings when you create the element. The connector opens the connection to the analyzer itself, with the settings on the **General** page.

A VISA library (R&S VISA or NI-VISA) must be installed on every DataMiner Agent that hosts an element of this connector. VISA is not included in the connector package. Without it, the connection fails. For a LAN/GPIB gateway, the VISA library must also be able to reach the gateway, e.g., with the Keysight IO Libraries.

### Initialization

After you have created the element, configure the connection on the **General** page:

1. In the **IP Address** box, enter the IP address of the analyzer. For GPIB via LAN Gateway, enter the IP address of the gateway instead.

1. In the **Connection Type** list, select the connection type:

   - **VXI-11** (default): For an analyzer on the LAN. This is the LAN protocol documented for the R&S FSL, and the recommended connection type.
   - **Raw Socket**: For an analyzer on the LAN when VXI-11 cannot be used. See [Notes](#notes).
   - **GPIB via LAN Gateway**: For an analyzer with option FSL-B10 on a GPIB bus behind a LAN/GPIB gateway, e.g., a Keysight E5810A.

1. For Raw Socket, set **Port** to the TCP port of the analyzer (default *5025*). When the port is empty or invalid, port 5025 is used.

1. For GPIB via LAN Gateway, set **GPIB Address** to the GPIB address of the analyzer (0 to 30, default *20*).

   The connector will connect to the analyzer and fill in **Manufacturer**, **Model**, **Serial Number**, **Firmware Version**, and **Installed Options**.

HiSLIP is not supported. See [Notes](#notes).

## How to Use

### Spectrum Analysis

To view traces and change the analyzer settings, open the element in the Spectrum Analysis module. The connector supports the standard spectrum analyzer features, such as spectrum presets, measurement points, and spectrum scripts. For more information, see [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

The measurement settings (frequencies, span, reference level, scale, attenuation, RBW, VBW, sweep time, sweep points, detection mode, and scale type) are not shown on the **General** page. You change them in the Spectrum Analysis module.

The attenuation, RBW, VBW, and sweep time can be set to *Auto*. The Spectrum Analysis module then shows the value selected by the analyzer, e.g., the actual RBW and VBW in Hz.

The detection mode is applied as soon as you set it. You can select *Auto* or one of the seven detectors of the analyzer. The connector never changes the detector by itself. After a preset, the analyzer uses *Auto Peak*.

The RBW values 10 Hz, 30 Hz, and 100 Hz need option FSL-B7. The connector shows these values when the analyzer uses them, but you cannot select them.

### General Page

The **General** page contains the connection settings and the device identity, as well as these parameters:

- **Display Status**: Switches the analyzer display on or off during a measurement.
- **DMS Spectrum Measurements**: When set to *Inhibited*, DataMiner no longer starts any spectrum measurements on the analyzer, and the analyzer is set to continuous sweep. The next poll sets the analyzer back to the **Sweep Mode** setting. By default, *Inhibited* raises a warning alarm.
- **Sweep Mode**: *Single* or *Continuous*. The connector keeps the analyzer in the sweep mode you set. If the sweep mode is changed on the analyzer itself, the connector restores it at the next poll.
- **Zero Span Start Sweep**: Sets the span to 0 and starts a zero span acquisition at the center frequency. If the frequency setting is rejected, the sweep does not start.
- **Preset**: Resets the analyzer to its default settings and reads back all settings. You need to confirm this action.
- **LO Offset** and **LO Side**: Translate between RF and the frequencies of the analyzer. See [Working with RF frequencies](#working-with-rf-frequencies).
- **Reference Source**: *Internal* or *External* frequency reference.
- **IF Overload**: Indicates that the IF stage of the analyzer is overloaded. The measured levels are then not reliable. To solve this, increase the attenuation or the reference level, or reduce the input signal.
- **External Reference Status**: Indicates whether the external reference signal is missing or unlocked. This is only relevant when **Reference Source** is set to *External*.
- **Last Rejected Setting**: The last setting that was not applied, with the date and time (local time of the DataMiner Agent) and the reason. This covers values outside the range of the analyzer and values the analyzer refused, e.g., a reference level that is too high for the input attenuation. The parameter is empty until a setting is rejected, and it is not cleared when a later setting is applied.
- **Debug**: Shows the **Debug** page. See [Debug page](#debug-page).

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

The connector uses the frequency range of the FSL18: 9 kHz to 18 GHz. The range does not depend on the model reported by the analyzer.

Before the connector sends any frequency to the analyzer, it converts the center, start, and stop frequency and checks them against this range. When you set a center frequency and span together, without a start and stop frequency, or in zero span, the edges of the span are checked too. These edges can go from 0 Hz up to 18 GHz. The overrange of the analyzer above 18 GHz is not accepted. A negative RF frequency is always rejected.

If one of these values is out of range, the whole frequency setting is rejected and no frequency is sent to the analyzer. The other settings are still applied. The reason is shown in **Last Rejected Setting**, and the element log shows the RF value, the LO Offset, the LO Side, and the device value. The check also applies when **LO Offset** is 0.

With an LO, the valid RF range moves with the LO:

- **Low Side**: from 9 kHz + LO up to 18 GHz + LO. For example, with an LO of 9750 MHz, the connector accepts 9750.009 MHz to 27750 MHz.
- **High Side**: from LO - 18 GHz up to LO - 9 kHz.

The connector also checks these settings against the FSL18 data sheet before it sends them:

- **Reference level**: -80 dBm to +20 dBm.
- **Input attenuation**: *Auto*, or 0 dB to 40 dB in steps of 5 dB.
- **Sweep points**: 101 to 32001.

A value outside these ranges is rejected and shown in **Last Rejected Setting**. It is not rounded or limited to the nearest valid value. The other settings are limited by the ranges of the parameters.

### Debug Page

The **Debug** page helps you find out why an element loses the connection to the analyzer. It is hidden by default. To show it, set **Debug** on the **General** page to *Enabled*.

Debug turns off by itself after 30 minutes. **Debug Auto off Time** shows when this happens (UTC). Debug is also disabled after an element restart. Enabling Debug sends nothing to the analyzer.

The **Debug** page shows:

- The connection and acquisition state, and the last operation on the analyzer.
- **Command History**: The last commands sent to the analyzer, with their timing. Only the command headers are kept, without arguments or replies.
- **TCP Connections**: The TCP connections from the DataMiner Agent that hosts the element to the configured IP address, with the process that holds each connection. Click **Refresh TCP Connections** to take a new snapshot. This only covers the local DataMiner Agent. Controllers on other computers are not shown.
- **Raw Command**: Sends one read-only query from a fixed list, e.g., `*IDN?` or `:FREQ:CENT?`, and shows the reply in **Raw Reply**. Any other command is refused and not sent. The query is also refused while there is no connection, while the connector recovers the connection, and while an acquisition is pending, i.e., a sweep or a zero span acquisition is running. Stop the spectrum acquisition before you use it. Frequency replies are device values, not RF values.

After a communication failure, the connector also writes the command history and the TCP connections to the element log, at most once per minute, even when Debug is disabled. Disable Debug when you are done.

### Moving an Existing FSL18 Element to This Connector

If an FSL18 is currently monitored with another connector, e.g., the Rohde Schwarz FSL3 connector, you need to create a new element with this connector. An element cannot be changed to a connector with another name.

1. Note the settings of the old element: the IP address, the connection type and port, the sweep mode, the **LO Offset**, the **LO Side**, and the alarm and trend templates.

1. Create a new element with this connector, and configure the connection as described under [Initialization](#initialization).

   A new element starts with the default settings: VXI-11, an **LO Offset** of 0, and *Low Side*.

1. Set **Sweep Mode**, **LO Offset**, and **LO Side** again.

1. Update the spectrum presets, measurement points, Visual Overview pages, and scripts that refer to the old element, so that they refer to the new element.

1. Check the values written by scripts against the [setting limits](#setting-limits) of the FSL18.

1. Stop the old element when the new element works. Do not connect both elements to the same analyzer at the same time.

The parameter IDs are the same as in version 2.0.0.2 of the Rohde Schwarz FSL3 connector.

## Notes

- **VXI-11** is the recommended connection type. **Raw Socket** worked on an FSL18 in a test with 20-second sweeps, without timeouts. On an FSL3, the analyzer once stopped answering on its socket port after a timeout, until *LOCAL* was pressed on the front panel or the analyzer was restarted. This issue is under investigation. VXI-11 recovers from a timeout by itself.
- **HiSLIP** is not documented for the R&S FSL and is not supported. An element with the HiSLIP connection type of the Rohde Schwarz FSL3 connector, e.g., after a copy of the settings, does not connect until you select another connection type.
- A GPIB card in the DataMiner Agent cannot be used directly. Use a LAN/GPIB gateway instead.
- After an element restart, the center, start, and stop frequency can be empty until the next poll or until you apply new settings.
- We recommend DataMiner 10.5.0 CU21, 10.6.0 CU9, 10.6.12, or later, with the matching DataMiner Cube version. These versions contain several fixes in the Spectrum Analysis module for spectrum presets and shared mode. See [DataMiner Cube 10.6.12](https://docs.dataminer.services/release-notes/Cube/Cube_Feature_Release_10.6/Cube_10.6.12.html), RN 46514, 46516, 46555, 46585, and 46668.
