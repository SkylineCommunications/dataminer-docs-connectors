---
uid: Connector_help_Volkert_Multi-Streamer_Technical
---

# Volkert Multi-Streamer

## About

Multi-Streamer (by Volkert Software) is a cross-platform application for handling real-time multimedia streams.
The connector monitors all Media Source details and has the capability to add/remove new media sources as well as pausing or muting.

## Configuration

### Connections

#### IP Connection - TCP

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (Default *9111*)]

## How to use

This connector monitors all configured Media Sources and it's streaam details such as bitrates, codec parameters, etc.
The Multi-streamer requires a password to successfully authenticate which can be filled in on the **Authentication**-section.
