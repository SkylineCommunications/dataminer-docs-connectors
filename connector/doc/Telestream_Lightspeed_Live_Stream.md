---
uid: Connector_help_Telestream_Lightspeed_Live_Stream
---

# Telestream Lightspeed Live Stream

Telestream Lightspeed Live Stream is an enterprise-class live streaming system. It can ingest, encode, package, and deploy multiple sources to multiple destinations. Lightspeed Live Stream allows quality and adaptive bitrate encoding of SD, HD, and UHD sources into AVC (H.264) and HEVC (H.265).

## About

### Version Info

| Range                                | Features                                              | Based on | System Impact |
|--------------------------------------|-------------------------------------------------------|----------|---------------|
| 1.0.0.x [**Obsolete - see 1.0.1.x**] | Initial version.                                      | -        | -             |
| 1.0.1.x [SLC Main]                   | New version because of invalid connector development. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |
| 1.0.1.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 |                     |
| 1.0.1.x | No              | Yes                 | -                 |                     |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *8089*).

### Initialization

To be able to log in, specify the **API token** on the **Authentication** page. The API token can be found in the web app's **About** panel, accessible from the settings menu.

### Web Interface

The web interface is only accessible when the client machine has network access to the product. To access the web interface, the default port 8089 is used. You can modify this by setting a different port with the **Live Stream Web Application Port** parameter.

## How to use

On the **General** page, the **Machines** table provides an overview of all available Live Stream servers.

A table listing sources can be found on the **Sources** page. Similarly, you can find a table listing encoders on the **Encoders** page, and a table listing packages on the **Packages** page. The **Encoders** page also contains a **Streams** tables, and the **Packages** page a **Variants** table.

**Channels**, **Channel Source**, and **Streaming Destinations** tables can be found on the **Channels** page. This page also contains a page button to the **Channels Overview** subpage.

## Notes

For certain requests, a 404 response is expected to be received. This will for example occur for requests to retrieve a certain channel's health information.
