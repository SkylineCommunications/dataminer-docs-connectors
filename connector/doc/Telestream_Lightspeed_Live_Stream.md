---
uid: Connector_help_Telestream_Lightspeed_Live_Stream
---

# Telestream Lightspeed Live Stream

Telestream Lightspeed Live Stream is an enterprise-class live streaming system. It can ingest, encode, package and deploy multiple sources to multiple destinations. Lightspeed Live Stream provides exceptional quality and adaptive bitrate encoding for SD, HD, UHD sources into AVC (H.264) and HEVC (H.265). Thanks to a mixture of hardware and software this system combines multiple CPU/GPU cores as well as targeted ASIC CODEC acceleration to deliver flexible and efficient encoding performance.

## About

### Version Info



|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [**Obsolete - see 1.0.1.x**]     |<ul><li>Initial version</li>        |-         |-         |
|1.0.1.x [SLC Main]     |<ul><li>New version because of invalid connector development.         |-         |-         |

### Product Info


|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |-        |
|1.0.1.x     |-        |


### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |
|1.0.1.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *8089*)]


### Initialization

To be able to log int specify the **API token** on the **Authentication** page.


### Web Interface

The web interface is only accessible when the client machine has network access to the product. To be able to access is the default port 8089 is being used.
This can be modified by setting a different port on the **Live Stream Web Application Port** parameter.

## How to use

On the **General** page, the **Machines** table provides an overview of all available Live Stream servers.

**Sources** page contains **Sources** table.

**Encoders** page contains **Encoders** and **Streams** tables.

**Packages** page contains **Packages** and **Variants** tables.

**Channels**, **Channel Source** and **Streaming Destinations** tables can be found on the **Channels** page which also contains a page button for the **Channels Overview** subpage.

## Notes

For certain requests it is expected to receive 404 response, such as request for retrieving certain channel's health information. 


