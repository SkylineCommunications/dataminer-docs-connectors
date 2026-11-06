---
uid: Connector_help_Calian_Multiport_Decimator_Technical
description: "Configure the Calian Multiport Decimator connector in DataMiner: socket API connection, Spectrum Analysis usage, ports, and down converter offsets."
---

# Calian Multiport Decimator

## About

The Calian Multiport Decimator D4 is an FFT-based spectrum analyzer with 4 or 8 RF inputs behind an internal switch. This connector uses the legacy socket API of the D4 to select the active input, configure the spectrum measurement, and request traces. The traces and settings are available in the DataMiner Spectrum Analysis module.

The connector does not export child elements (DVEs).

> [!NOTE]
> Calian was formerly SED Systems. The [SED Decimator 8 port](xref:Connector_help_SED_Decimator_8_port) and [SED Decimator 16 port](xref:Connector_help_SED_Decimator_16_port) connectors are separate connectors.

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection over TCP/IP (**IP Connection**) and requires the following input during element creation:

- **Type of port**: *TCP/IP*. Other port types are not available.
- **IP address/host**: The management IP address of the D4.
- **IP port**: *9784*. This is the port of the legacy socket API. The field cannot be changed.
- **Bus address**: Not required.

The legacy socket API has no authentication, so no credentials are needed.

### Initialization

Before you create the element, open the D4 web GUI and make sure that the legacy socket API is enabled on the **Remote Access** tab. If the API is disabled, the element goes into timeout without any other error.

Keep the following in mind:

- The D4 limits the number of API clients. Every DataMiner element and every other tool connected to port 9784 counts as a client.
- Settings sent over the socket API only apply to that client session. After a reconnection, a timeout, or a soft or hard reset, the connector sends its settings to the device again: active input, spectral inversion, reference clock, attenuation, maximum capture time, and the spectrum settings. Settings changed directly on the device while DataMiner is connected are therefore overwritten by the DataMiner values after a reconnection.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### Spectrum Analyzer

The element is a spectrum analyzer element. Open it in the DataMiner Spectrum Analysis module to see the trace of the active input and to change the measurement settings. For more information, refer to [Working with spectrum analyzer elements](https://aka.dataminer.services/Working_with_spectrum_analyzer_elements).

Keep the following in mind:

- **Traces on request**: The D4 does not sweep continuously over the socket API. Each trace is a new measurement that the Spectrum Analysis module requests. The polling rate of the module determines how often the trace is updated. There is no sweep time setting and no zero span.
- **Resolution bandwidth (RBW)**: In manual mode, the device uses the RBW you set. In automatic mode, the device selects the RBW that gives about **Auto RBW Points** points over the span.
- **Video bandwidth (VBW)**: The D4 has no VBW filter. It averages several spectra instead. In manual mode, the device calculates the number of averages for the VBW you set. In automatic mode, the device uses **Number of Averages**, and the VBW is shown as *-1* (Auto).
- **Reference level and scale**: These are display settings only. They are never sent to the device. You can enter any reference level from -200 to 50 dBm. A value outside this range is rejected and logged.
- **Invalid traces**: A trace is only shown when its length matches the length reported by the device and all values are valid. Otherwise, the previous trace stays visible and the reason is logged.

### Frequency Limits

The connector checks every frequency change before it sends anything to the device. It uses the frequency and span limits reported by the device. Until the device has reported its limits, the connector uses 5 MHz to 6.5 GHz. With a down converter offset, the valid range is the device range plus the offset of the active input.

- **Center frequency out of range**: The whole change is rejected and nothing is sent. The center frequency, span, RBW, and VBW go back to the values confirmed by the device, and the reason is logged in the element log.
- **Span**: A span outside the device limits is replaced by the last confirmed span. The span is also reduced when needed, so that the start and stop frequencies stay inside the valid range.
- **Start and stop frequency**: These are calculated from the center frequency and span confirmed by the device. They only change after the device confirms the new settings.

### Down Converter Offset

When a down converter is placed in front of an input, enter its offset so that you see and set RF frequencies:

1. Go to the **Ports** page.
1. In the **Switch Ports** table, enter the **Down Converter Frequency Offset** in MHz for each input that has a down converter.
1. On the **General** page, select the input with **Active Switch**.

   The center, start, and stop frequency in the Spectrum Analysis module will now include the offset of the active input.

The connector applies the offset as follows:

- The offset is added to the device frequency to show the RF frequency: RF = device frequency + offset. When you set a center frequency, the offset is subtracted before the value is sent to the device.
- The span is never changed by the offset.
- An offset of *0* means no translation.
- Only low-side conversion is supported. The connector has no LO Side setting and does not reverse the trace, so high-side (spectrum inverting) down converters are not supported.

> [!WARNING]
> Do not also configure a down converter frequency on the D4 itself (web GUI, **Calibration** tab). The D4 then adds its own value as well, and the offset is counted twice. Use either the connector offset or the device setting, not both.

### General Page

This page shows the active input and the device status, and contains the main device settings:

- **Active Switch** and **Active Switch Port Name**: The selected input. Use **Active Switch** to select another input.
- **Spectral Inversion**, **Reference Clock**, **Attenuation Mode**, and **Attenuation Level**: Device settings. The attenuation range is read from the device.
- **Detector**: Select *Average* (default) or *Peak*. Peak shows noise and digital carriers a few dB higher. Use the same detector when you compare traces.
- **Auto RBW Points**, **Number of Averages**, and **Maximum Capture Time**: Settings for the automatic RBW and VBW modes and for the capture length. **Maximum Capture Time** can be set from 1 to 60 seconds (default: *10*). When a capture would take longer, the device refuses it.
- **Estimated Capture Time**: The capture time that the device expects for the current settings. The connector adjusts its trace timeout to this value.
- **Actual** and **Effective** values: The center frequency, span, RBW, VBW, and number of averages that the device confirmed.
- **Last Device Error**, **Last Device Error Time**, and **Last Device Error Time UTC**: The last error returned by the device. When the device returns an error during a settings change, the rest of the change is skipped.
- Device health: firmware and software version, serial number, device status, temperature, calibration status, and power supply voltages.
- **Soft Reset Button** and **Hard Reset Button**: Trigger a soft reset (of the software API) or a hard reset of the device, after confirmation. The connection drops, and the connector sends its settings again when the device is back.
- **Debug**: Shows the Debug page. See [Debug Page](#debug-page).

If a trace stops after a settings change, check **Estimated Capture Time** and **Last Device Error**. A small RBW or many averages make the capture slower. Use fewer averages or a larger RBW, or increase **Maximum Capture Time**.

### Ports Page

The **Switch Ports** table lists the inputs of the device with their names and the **Down Converter Frequency Offset** of each input.

### Debug Page

This page is meant for troubleshooting with DataMiner support. It is hidden by default.

1. On the **General** page, set **Debug** to *Enabled*.

   The **Debug** page will appear, and **Debug Auto off Time** will show when debug mode switches off.

1. On the **Debug** page, enter a command in **Raw Command** and set it.

   The device reply and the round-trip time will be shown.

The raw command console only accepts read-only commands from a fixed list, e.g., `status`, `getConfig`, `getLimits`, `captureTime`, and `getUserCount`. Commands that change or reset the device are refused and logged. The page also shows trace statistics, such as the time between traces and the trace size.

Debug mode adds detailed lines (starting with `DEBUG|`) to the element log. It is not saved: it is off after an element restart, and it switches off automatically after 30 minutes.

## DataMiner Connectivity Framework

This connector defines the following fixed DCF interfaces.

### Interfaces

#### Fixed Interfaces

| Interface | Type |
|--|--|
| J1 to J8 | in/out |

## Notes

- This connector requires DataMiner 10.4.0.0 (build 14003) or later. From range 1.0.1.x, the connector name changed from "Calian Decimator D4" to "Calian Multiport Decimator": update any configuration that refers to the old name, and check whether a license change is needed.
- The connector uses the legacy socket API only. The HTTPS REST API and the secure socket API of the D4 are not used.
- Measurements such as band power, C/N, cross-polarization, and demodulation are not available through this connector.
- Single-port D4 models and the Decimator D3 or older models have not been qualified with this connector.
