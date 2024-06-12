---
uid: Connector_help_Ateme_Titan_Edge_-_Gateway
---

# Ateme Titan Edge - Gateway

This connector is exported by the parent connector [Ateme Titan Edge](xref:Connector_help_Ateme_Titan_Edge).

## About

### Version Info

| Range              | Key Features                                                                                   | Based on | System Impact |
|--------------------|------------------------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x            | Initial version.                                                                               | -        | -             |
| 1.0.1.x [SLC Main] | Implemented firmware version 2.11.1. Primary key changes for Video Input Configuration tables. | 1.0.0.4  | -             |
| 1.0.2.x            | Encoder and Gateway IP Output table PK changed. Layout adapted.                                | 1.0.1.10 | -             |
| 1.1.0.x            | API structure changed to match new software version device.                                    | 1.0.2.3  | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | API v0.1               |
| 1.0.1.x   | API v0.1               |
| 1.0.2.x   | API v0.1               |
| 1.1.0.x   | API ??? Software v3.0.2|

## Configuration

This connector is used by DVE child elements that are **automatically created** by the connector [Ateme Titan Edge](xref:Connector_help_Ateme_Titan_Edge).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element created with this connector has the following data pages:

- **General**: Displays information about the gateway status.
- **Gateway Input**: Displays information about the inputs.
- **Gateway Probe Overview**: Contains a tree view of the programs captured by the probe.
- **Gateway Probe Information**: Displays information about the decoder programs and PIDs.
- **Gateway Output**: Contains information about the outputs.
- **Gateway Configuration**: Allows you to configure settings for the gateway.
