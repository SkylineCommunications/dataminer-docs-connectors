---
uid: Connector_help_Broadpeak_BKS350
description: Monitor the Broadpeak BKS350 packager streamer in DataMiner, with real-time visibility of server status, live streaming, outputs, and device alarms.
---

# Broadpeak BKS350

## About

Broadpeak BKS350 is a packager streamer that improves multi-screen video delivery on managed or open internet networks. It prepares and publishes live and on-demand content in the formats required by the various client devices in a video delivery chain.

This connector brings the operational state of the BKS350 into DataMiner, so that you can follow server health, live streaming activity, and delivery performance from the same platform you use for the rest of your video chain.

## Key Features

- **Server status monitoring**: Follow general device information, such as the current date and time and the uptime, together with the overall status of the equipment.
- **Live streaming visibility**: Track all live status parameters to confirm that streams are being packaged and delivered as expected.
- **Output and publishing insight**: Monitor output status with the associated template name and output format, along with all publishing status parameters.
- **Service performance statistics**: Consult the statistics collected by the device to assess delivery performance over time.
- **Device-reported alarm surfacing**: Retrieve the alarms raised by the BKS350 itself, including the ones logged while the device was operational, without having to open its own interface.

## Use Cases

### Detecting Live Streaming Issues Before Viewers Do

**Challenge**: In a multi-screen delivery chain, a packager streamer problem can degrade playback for a large group of viewers before anyone reports it.

**Solution**: Monitor the live, output, and publishing status of the BKS350 in DataMiner, combined with the alarms reported by the device.

**Benefit**: Operators see a stream that stops being packaged or published correctly straight away, so they can react while the issue is still limited to a single component.

### Centralizing Packager Monitoring Across the Video Chain

**Challenge**: Checking the health of a packager streamer on its own web interface keeps it separate from the rest of the video delivery monitoring.

**Solution**: Bring server status, uptime, and service performance statistics of the BKS350 into the same DataMiner System used for the surrounding equipment.

**Benefit**: Teams assess delivery performance from a single platform, without having to log in to the device to establish its state.

## Technical Reference

### Prerequisites

- This connector requires **DataMiner version 10.4.0.0 - 14003** or higher.
- **SNMP access** to the BKS350 is required, including the get and set community strings configured on the device.
- **HTTP access** to the BKS350 is required for the polling IP or URL and the IP port of the device.

> [!NOTE]
> For detailed technical information, refer to the [Broadpeak BKS350 Technical](xref:Connector_help_Broadpeak_BKS350_Technical) page.
