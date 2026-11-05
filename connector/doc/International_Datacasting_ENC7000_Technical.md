---
uid: Connector_help_International_Datacasting_ENC7000_Technical
---

# International Datacasting ENC7000

## About

The International Datacasting ENC7000 Audio Encoder is designed to encode multiple audio channels into MPEG-4 AAC-LC, HE-AAC v1/v2, and MPEG-1 Layer 2 formats for improved IP audio delivery. It supports up to 12 digital stereo channels or up to 8 analog stereo channels, which can be output as MPEG-2 compliant DVB transport streams or elementary streams via the IP interface. The encoder can be managed remotely through REST API, ensuring flexible and efficient audio data transmission across various network configurations.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).

### Initialization

To be able to access the device, specify a correct username and password on the **General** page.

## How to use

The following pages are available:

- The **General** page contains authentication and system parameters.
- On the **Versions** page, you can find the current image and software versions.
- The **Interfaces** page shows a list of all available interfaces.
- The **Inputs** page contains a table with different types of inputs. Two types, **Web Streams** and **Transport Streams**, are supported and can be configured on the corresponding subpages.
- The **Input Selectors** page contains a table with all input selectors.
- The **Encoders** page contains two tables, one for monitoring and one for configuring encoders. An encoder must have a reference to either an input selector (Input Selectors table) or an audio source (Inputs table).
- The **MPEG-2 TS** page contains a table with transport streams. Each transport stream can have multiple destinations and services, which can be managed on the **Destinations** and **Services** pages.
- The **File Manager** page lists the available files.

Most of the tables have a right-click menu available that offers extra functionality such as adding, editing, or deleting an entry.
