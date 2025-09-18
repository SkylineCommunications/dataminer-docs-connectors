---
uid: Connector_help_Volkert_Multi-Streamer_Technical
---

# Volkert Multi-Streamer

## About

Multi-Streamer (by Volkert Software) is a cross-platform application for handling real-time multimedia streams. This connector monitors all media source details and allows users to add or remove media sources as well as pause or mute them.

## Configuration

### Connections

#### IP Connection - TCP

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination (default *9111*).

### Initialization

The Multi-streamer requires a password to successfully authenticate, which should be filled in in the **Authentication** section.

## How to use

This connector monitors all configured media sources and their stream details such as bitrates, codec parameters, etc.
