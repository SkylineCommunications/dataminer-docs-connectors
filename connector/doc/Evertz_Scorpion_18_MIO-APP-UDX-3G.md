---
uid: Connector_help_Evertz_Scorpion_18_MIO-APP-UDX-3G
---

# Evertz Scorpion 18 MIO-APP-UDX-3G

## About

The Evertz MIO-APP-UDX-3G is a processing application for the Scorpion 18 platform that converts, corrects, and conditions video, audio, and ancillary data on its way through a broadcast facility. It handles tasks such as up/down/cross-conversion, HDR/SDR conversion, audio shuffling and loudness control, and closed captioning and teletext handling, for both SDI and IP signals.

This connector brings the MIO-APP-UDX-3G into DataMiner, giving operators a single place to see the health of every signal passing through the module and to adjust its processing without having to log in to the device itself.

## Key Features

- **End-to-end signal health**: See at a glance whether video, audio, ancillary data, and the reference signal are arriving as expected, with alarms on missing signals, audio group loss, IP stream errors, caption and teletext faults, and high temperature.

- **Central control of video processing**: Adjust scaling, aspect ratio and AFD handling, deinterlacing, noise reduction, color correction, and HDR/SDR conversion directly from DataMiner, so picture quality can be tuned without going to the device.

- **Custom HDR/SDR looks**: Upload and select your own 3D lookup tables (LUTs), identified by their file names, to apply a consistent house look across HDR and SDR deliverables.

- **Audio control and loudness management**: Manage audio routing, mixing, downmix and upmix, and Intelligain loudness control, keeping audio levels compliant and consistent for viewers.

- **Caption, teletext, and time code assurance**: Monitor and configure closed captions, WST teletext, and time code, helping you to meet accessibility and regulatory obligations.

- **Presets**: Save and recall module configurations, making it fast and repeatable to switch between production setups.

## Use Cases

### Consistent HDR and SDR Delivery

**Challenge**: Delivering both HDR and SDR versions of the same content requires accurate conversion settings, and mismatched settings across modules lead to visible differences in picture quality.

**Solution**: Operators review and adjust the HDR/SDR conversion settings and custom 3D LUTs of every MIO-APP-UDX-3G module from DataMiner.

**Benefit**: A consistent picture across all outputs and faster corrections when a look needs to change.

### Loudness and Audio Compliance

**Challenge**: Audio arriving from different sources varies in level and channel layout, risking loudness complaints and non-compliance.

**Solution**: Intelligain loudness control, downmix, and upmix settings are configured and monitored centrally, with alarms when audio groups or programs go missing.

**Benefit**: Compliant, predictable audio for viewers and early warning before an audio issue goes on air.

### Accessibility Services Assurance

**Challenge**: Missing closed captions or teletext often go unnoticed until viewers complain, which can result in regulatory penalties.

**Solution**: DataMiner continuously monitors caption and teletext presence and raises alarms on faults.

**Benefit**: Accessibility problems are detected and resolved quickly, protecting both the audience experience and regulatory standing.


## Technical Reference

### Prerequisites

- **SNMP access** to the Scorpion 18 device is required for DataMiner to monitor and control the MIO-APP-UDX-3G.

- **Network access** from the client machine to the device is required to open the device's web interface from DataMiner.


> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Evertz_Scorpion_18_MIO-APP-UDX-3G_Technical).