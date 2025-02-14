---
uid: Connector_help_Warner_Bros_Discovery_DAZN_Live_Stream_API_Technical
---

# Warner Bros Discovery DAZN Live Stream API

The Warner Bros Discovery Sports DAZN Live Stream API connector can be used to ingest and display the DAZN Live feeds (https://docs.daznservices.com/docs/live/index.html).

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 1.0                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components                                      | Exported Components |
|---------|-----------------|---------------------|--------------------------------------------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                                                      |                     |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

## How to use

This connector parses the live feeds from the DAZN Live Feeds API and display the details within the **Live Feeds Table**.
Each live feed can have one or multiple audio tracks which are displayed in the **Audio Tracks Table**.

It's possible to tweak the API retrieval method by updating the following parameters under the **Configuration** page:
- Authentication Key: key used as authentication for the API requests
- Operating Mode: [B2B] or [B2C] request mode
- Live Event Schedule Depth (days): filters the feeds with a start time in the future which fall within the defined days starting from the current date
- Field Mask: properties to return from the API (see https://docs.daznservices.com/docs/live/index.html).

On the **Poll Settings** page, it's possible to tweak the polling interval of each defined item.
