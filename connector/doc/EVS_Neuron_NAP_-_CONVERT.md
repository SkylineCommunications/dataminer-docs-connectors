---
uid: Connector_help_EVS_Neuron_NAP_-_CONVERT
---

# EVS Neuron NAP - CONVERT

## About

The EVS Neuron NAP - CONVERT connector enables real-time monitoring and control of Neuron Convert devices, which provide high-density video and audio format conversion. This connector allows broadcast operators to manage and supervise conversion operations efficiently within their broadcast environments.

## Key Features

- **Comprehensive device monitoring**: Access detailed device identity, firmware version, and API information for Neuron Convert devices.
- **Video path and channel monitoring**: Gain full visibility into video processing paths and their associated channels, including input selection, lock status, output format, and deinterlacing settings.
- **Input format tracking**: Monitor the active, main, and backup input formats per video channel to quickly detect and respond to format mismatches or failovers.
- **Advanced video processing configuration**: Configure and monitor delay and frame sync settings, audio embedders, RGB gain and color correction, HDR color space conversion, and scaling per video channel.
- **Flexible polling management**: Use the built-in Polling Manager to control how frequently each data group is retrieved from the device, with support for on-demand polling.

## Use Case

**Challenge**: Managing and monitoring complex video format conversion operations across multiple channels in a broadcast environment, where format mismatches or misconfigured processing settings can lead to on-air issues.

**Solution**: The connector provides centralized monitoring and configuration of Neuron Convert devices, offering a structured overview of video processing paths, channels, and their detailed settings — all from within DataMiner.

**Benefit**: Reduces operational overhead and accelerates fault detection by consolidating all conversion device data into a single element, enabling operators to quickly identify misconfigurations or format issues across all channels.

## Technical Reference

### Prerequisites

- **Network connectivity** is required for IP-based monitoring and control.
- **Firmware version 6.x** is required.
- **DataMiner version 10.4.0** or higher is required.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_EVS_Neuron_NAP_-_CONVERT_Technical).
