---
uid: Connector_help_Ateme_Titan_Edge_-_Decoder
---

# Ateme Titan Edge - Decoder

This connector is exported by the parent connector [Ateme Titan Edge](xref:Connector_help_Ateme_Titan_Edge).

## About

### Version Info

| Range              | Key Features                                                                                   | Based on | System Impact |
|--------------------|------------------------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x            | Initial version.                                                                               | -        | -             |
| 1.0.1.x            | Implemented firmware version 2.11.1. Primary key changes for Video Input Configuration tables. | 1.0.0.4  | -             |
| 1.0.2.x            | Encoder and Gateway IP Output table PK changed. Layout adapted.                                | 1.0.1.10 | -             |
| 1.1.0.x            | API structure changed to match new software version device.                                    | 1.0.2.3  | -             |
| 1.1.1.x [SLC Main] | API structure changed to match new software version device.                                    | 1.1.0.4  | -             |

### Product Info

| Range   | Supported Firmware            |
|---------|-------------------------------|
| 1.0.0.x | API v0.1                      |
| 1.0.1.x | API v0.1                      |
| 1.0.2.x | API v0.1                      |
| 1.1.0.x | API unknown - Software v3.0.2 |
| 1.1.1.x | API unknown - Software v3.0.2 |

## Configuration

This connector is used by DVE child elements that are **automatically created** by the connector [Ateme Titan Edge](xref:Connector_help_Ateme_Titan_Edge).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element created with this connector has the following data pages:

- **General**: Displays information about the decoder status.
- **Decoder Input**: Displays information about the inputs
- **Decoder Probe Overview**: Contains a tree view of the programs captured by the probe.
- **Decoder Probe Information**: Displays information about the decoder programs and PIDs.
- **Decoder Video**: Contains information about the SDI and video.
- **Decoder Audio**: Contains information about the audio.
- **Decoder Progrm**: Contains information about the programs.
- **Decoder Configuration**: Allows you to configure settings for the decoder.
