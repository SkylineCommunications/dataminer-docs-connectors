---
uid: Connector_help_Agilent_N9010A-526_EXA_Technical
description: "Configure the Agilent (Keysight) N9010A-526 EXA connector in DataMiner: VISA connections, RF frequency translation, setting limits, and troubleshooting."
---

# Agilent N9010A-526 EXA

## About

The **Agilent N9010A-526 EXA** connector monitors and controls the Agilent (Keysight) N9010A EXA signal analyzer with option 526 via SCPI commands. It shows the traces of the analyzer in the DataMiner Spectrum Analysis module, lets you change the analyzer settings, and shows the identity and installed options of the analyzer.

The connector does not export DVE child elements.

## Configuration

This connector requires DataMiner 10.4.0.0 - 14003 or higher.

### Connections

#### Virtual Connection

This connector uses a virtual connection. You do not need to configure any connection settings when you create the element. The connector opens the connection to the analyzer itself, with the settings on the **General** page.

A VISA library (e.g., Keysight IO Libraries, NI-VISA, or R&S VISA) must be installed on every DataMiner Agent that hosts an element of this connector. VISA is not included in the connector package. Without it, the connection fails.

### Initialization

After you have created the element, configure the connection on the **General** page:

1. In the **IP Address** box, enter the IP address of the analyzer.

1. In the **Connection Type** list, select the connection type:

   - **VXI-11** (default): For an analyzer on the LAN. VXI-11 allows only one controller at a time.
   - **HiSLIP**: For an analyzer with firmware A.11.00 or later. HiSLIP allows several controllers at the same time.
   - **Raw Socket**: For an analyzer on the LAN when VXI-11 and HiSLIP cannot be used.

1. For Raw Socket, set **Port** to the SCPI socket port of the analyzer. When the port is empty or invalid, port 5025 is used.

   The connector will connect to the analyzer and fill in **Manufacturer**, **Model**, **Serial Number**, **Firmware Version**, and **Installed Options**.

The selected server (VXI-11, HiSLIP, or socket) must be enabled on the analyzer, under **System** > **I/O Config** > **SCPI LAN**.

## How to Use

### Spectrum Analysis

To view traces and change the analyzer settings, open the element in the Spectrum Analysis module. The connector supports the standard spectrum analyzer features, such as spectrum presets, measurement points, and spectrum scripts. For more information, see [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

The measurement settings (frequencies, span, reference level, scale, attenuation, RBW, VBW, sweep time, and sweep points) are not shown on the **General** page. You change them in the Spectrum Analysis module.

The attenuation, RBW, VBW, and sweep time can be set to *Auto*. The Spectrum Analysis module then shows the value selected by the analyzer.

When the analyzer uses another power unit than dBm, the connector sets it to dBm.

### General Page

The **General** page contains the connection settings and the device identity, as well as these parameters:

- **Sweep Mode**: *Single* or *Continuous*. The connector keeps the analyzer in the sweep mode you set. If the sweep mode is changed on the analyzer itself, the connector restores it at the next poll.
- **Zero Span Start Sweep**: Sets the span to 0 and starts a zero span acquisition at the center frequency. A sweep that is still running is stopped first. If the frequency setting is rejected, the zero span acquisition does not start.
- **Preset**: Resets the analyzer to its default settings and reads back all settings. You need to confirm this action.
- **Installed Options**: The options reported by the analyzer, e.g., *503,507,513,526*.
- **LO Offset** and **LO Side**: Translate between RF and the frequencies of the analyzer. See [Working with RF frequencies](#working-with-rf-frequencies).
- **Detector**: *Auto* or one of the detectors of the analyzer. The detector is applied as soon as you set it. The connector never changes the detector by itself. *Power Average (RMS)* is the RMS detector of a standard EXA. *Quasi Peak*, *EMI Average*, and *RMS Average* need option EMC.
- **Last Rejected Setting**: The last setting that was not applied, with the date and time (local time of the DataMiner Agent) and the reason. This covers values outside the range of the analyzer and values the analyzer refused. The parameter is empty until a setting is rejected, and it is not cleared when a later setting is applied.
- **Debug**: Shows the **Debug** page. See [Debug page](#debug-page).

The connector checks the connection every 10 seconds. The identification, the installed options, the detector, and the sweep mode are read every 5 minutes.

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

The connector uses the frequency range of option 526: 10 Hz to 26.5 GHz (DC coupled). The connector does not know the input coupling. With AC coupling, the analyzer is specified from 10 MHz.

Before the connector sends any frequency to the analyzer, it converts the center, start, and stop frequency and checks them against this range. When you set a center frequency and span together, without a start and stop frequency, or in zero span, the edges of the span are checked too. These edges can go from 0 Hz up to 26.5 GHz. A negative RF frequency is always rejected.

If one of these values is out of range, the whole frequency setting is rejected and no frequency is sent to the analyzer. The other settings are still applied. The reason is shown in **Last Rejected Setting**, and the element log shows the RF value, the LO Offset, the LO Side, and the device value. The check also applies when **LO Offset** is 0.

With an LO, the valid RF range moves with the LO:

- **Low Side**: from 10 Hz + LO up to 26.5 GHz + LO.
- **High Side**: from LO - 26.5 GHz up to LO - 10 Hz.

The other settings follow the N9010A data sheet:

- **RBW**: *Auto*, 1 Hz to 3 MHz, and 4, 5, 6, and 8 MHz.
- **VBW**: *Auto*, 1 Hz to 3 MHz, 4, 5, 6, and 8 MHz, and 50 MHz (wide open).
- **Reference level**: -170 dBm to +23 dBm.
- **Scale**: 0.1 dB/div to 20 dB/div.
- **Input attenuation**: *Auto*, or 0 dB to 60 dB. A value between two steps is rounded up to the next 10 dB step (2 dB when **Installed Options** contains FSA), the same way the analyzer does it.
- **Sweep points**: 1 to 40001.

A sweep points value outside this range is rejected and shown in **Last Rejected Setting**. The other settings are limited by the ranges of the parameters.

### Debug Page

The **Debug** page helps you find out why an element loses the connection to the analyzer. It is hidden by default. To show it, set **Debug** on the **General** page to *Enabled*.

Debug turns off by itself after 30 minutes. **Debug Auto off Time** shows when this happens (UTC). Debug is also disabled after an element restart. Enabling Debug sends nothing to the analyzer.

The **Debug** page shows:

- The connection and acquisition state, and the last operation on the analyzer.
- **Command History**: The last commands sent to the analyzer, with their timing. Only the command headers are kept, without arguments or replies.
- **TCP Connections**: The TCP connections from the DataMiner Agent that hosts the element to the configured IP address, with the process that holds each connection. Click **Refresh TCP Connections** to take a new snapshot. This only covers the local DataMiner Agent. Controllers on other computers are not shown.
- **Raw Command**: Sends one read-only query from a fixed list, e.g., `*IDN?` or `:FREQ:CENT?`, and shows the reply in **Raw Reply**. Any other command is refused and not sent. The query is also refused while there is no connection, while the connector recovers the connection, and while an acquisition is pending, i.e., a sweep or a zero span acquisition is running. Stop the spectrum acquisition before you use it. Frequency replies are device values, not RF values.

After a communication failure, the connector also writes the command history and the TCP connections to the element log, at most once per minute, even when Debug is disabled. Disable Debug when you are done.

### Upgrading from Version 1.2.0.x

Version 1.2.1.1 starts a new range. Check the following before you upgrade an existing element:

1. **Connection Type**: The default changed from Raw Socket to VXI-11, and the parameter is renamed from **RS Connection Type** to **Connection Type**. After the upgrade, check the connection type on the **General** page. For Raw Socket, set **Connection Type** and **Port** explicitly.

1. **Setting ranges**: 10 MHz is no longer available for RBW and VBW, the reference level goes up to +23 dBm, and the scale goes up to 20 dB/div. Update spectrum presets and scripts that write values outside these ranges. Use 8 MHz (RBW) or 50 MHz (VBW, wide open) instead of 10 MHz.

1. **Sweep Mode**: The sweep mode is no longer saved or alarmed. Remove it from alarm templates. After an element restart, set **Sweep Mode** again if you do not use *Single*.

## Notes

- **VXI-11** allows only one controller at a time. When another application also controls the analyzer, use **HiSLIP** or make sure only one controller is active.
- The SCPI socket port is not documented in the vendor material. Port 5025 is the usual Keysight socket port. Set **Port** explicitly when the analyzer uses another port.
- After an element restart, the center, start, and stop frequency can be empty until the next poll or until you apply new settings.
- We recommend DataMiner 10.5.0 CU21, 10.6.0 CU9, 10.6.12, or later, with the matching DataMiner Cube version. These versions contain several fixes in the Spectrum Analysis module for spectrum presets and shared mode. See [DataMiner Cube 10.6.12](https://docs.dataminer.services/release-notes/Cube/Cube_Feature_Release_10.6/Cube_10.6.12.html), RN 46514, 46516, 46555, 46585, and 46668.