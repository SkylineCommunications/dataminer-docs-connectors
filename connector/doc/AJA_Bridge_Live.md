---
uid: Connector_help_AJA_Bridge_Live
---

# AJA Bridge Live

## About

The AJA Bridge Live connector enables seamless integration with AJA Bridge Live, a high-performance turnkey solution for SDI video encoding, decoding, transcoding, and streaming. Designed for remote production, live contribution, and content delivery, this connector allows users to monitor and configure critical workflows while ensuring reliable, cost-effective video transport across networks.

## Key Features

**System monitoring**: Retrieve system details such as software versions and real-time GPU/CPU utilization for performance monitoring.

**Network interface management**: Monitor network interfaces and bandwidth utilization, and ensure optimal connectivity for uninterrupted streaming.

**Pipeline control & configuration**: Start, stop, and modify pipelines dynamically, adjusting video, audio, and caption settings as needed.

**Input & output stream management**: Configure input and output streams with flexible encoding and transport options, including NDI, SRT, and RTMP.

## Use Cases

### Use Case 1: Replacing Satellite Uplink with IP Streaming

**Challenge**: Traditional satellite uplink solutions are expensive and require extensive infrastructure, making them inefficient for modern live broadcasts.

**Solution**: AJA Bridge Live allows broadcasters to replace satellite transponders with a simple ISP connection, leveraging bidirectional IP transport for reliable video streaming.

**Benefit**: Significant cost savings, reduced complexity, and improved flexibility for remote productions and live events.

### Use Case 2: Dynamic Multi-Codec Transcoding

**Challenge**: Live production environments require real-time transcoding across multiple formats to ensure compatibility with different platforms.

**Solution**: Bridge Live supports multiple codecs (H.264, HEVC, JPEG XS, MPEG-2) and can dynamically transcode streams to meet delivery requirements.

**Benefit**: Enhanced compatibility with CDNs like YouTube, Twitch, and Facebook Live, enabling seamless content distribution.

### Use Case 3: High-Redundancy Live Streaming

**Challenge**: Live video streams are vulnerable to network issues such as packet loss, jitter, and latency fluctuations.

**Solution**: With SMPTE 2022-7 hitless redundancy, AJA Bridge Live ensures seamless failover by transmitting identical streams across independent network paths.

**Benefit**: Increased reliability, reduced risk of video interruptions, and optimized quality of experience for viewers.

## Technical Reference

### Prerequisites

- Network access: AJA Bridge Live must be accessible over the network for API communication.
- Authentication configuration: Basic authentication credentials (username and password) must be set up.
- Pipeline configuration: Users should pre-define input and output settings for efficient stream management.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_AJA_Bridge_Live_Technical).
