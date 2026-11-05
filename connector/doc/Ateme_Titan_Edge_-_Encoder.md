---
uid: Connector_help_Ateme_Titan_Edge_-_Encoder
---

# Ateme Titan Edge - Encoder

This connector is exported by the parent connector [Ateme Titan Edge](xref:Connector_help_Ateme_Titan_Edge).

## About

### Version Info

| Range              | Key Features                                                                                   | Based on | System Impact |
|--------------------|------------------------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x            | Initial version.                                                                               | -        | -             |
| 1.0.1.x            | Implemented firmware version 2.11.1. Primary key changes for Video Input Configuration tables. | 1.0.0.4  | -             |
| 1.0.2.x            | Encoder and Gateway IP Output table PK changed. Layout adapted.                                | 1.0.1.10 | -             |
| 1.1.0.x            | API structure changed to match new software version device.                                    | 1.0.2.3  | -             |
| 1.1.1.x            | Added Decoder Video page with video parameters and added descrambling status for inputs.       | 1.1.0.4  | -             |
| 1.1.2.x            | Added additional Gateway Channel and Network parameters.                                       | 1.1.1.7  | -             |
| 1.1.3.x [SLC Main] | Fixes, naming improvements, and new decoder/encoder and Gateway parameters introduced.         | 1.1.2.10 | -             |

### Product Info

| Range   | Supported Firmware            |
|---------|-------------------------------|
| 1.0.0.x | API v0.1                      |
| 1.0.1.x | API v0.1                      |
| 1.0.2.x | API v0.1                      |
| 1.1.0.x | API unknown - Software v3.0.2 |
| 1.1.1.x | API unknown - Software v3.0.2 |
| 1.1.2.x | API unknown - Software v3.0.2 |
| 1.1.3.x | API unknown - Software v3.0.2 |

## Configuration

This connector is used by DVE child elements that are **automatically created** by the connector [Ateme Titan Edge](xref:Connector_help_Ateme_Titan_Edge).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element created with this connector has the following data pages:

- **General**: Displays information about the encoder status.
- **Encoder Input**: Displays information about the video and audio inputs.
- **Encoder Output**: Displays information about the IP, video, audio, and data outputs.
- **Encoder Configuration**: Allows you to configure settings for the encoder.
- **Encoder Video Input Config** / **Encoder Video Input SDI** / **Encoder Video Input SMPTE 2110** / **Encoder Audio Input Config** / **Encoder Audio Config**: These pages contain information and configuration parameters for the video input, SDI video inputs, SMPTE 2110 video inputs, audio input, and audio, respectively.
