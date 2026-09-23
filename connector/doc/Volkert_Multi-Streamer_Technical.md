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

### Enabling External Remote Control

External remote control must be enabled in the Volkert Multi-Streamer application for the connector to be able to successfully retrieve the stream details:

1. In the Volkert Multi-Streamer application, open **Settings** > **Remote Control**.

1. Enable **Allow to remote control this instance** and set a control password.

1. In the DataMiner element, enter the password in the **Authentication** section of the **General** page.

## How to use

This connector monitors all configured media sources and their stream details such as bitrates, codec parameters, etc.

### Flow routers

Media sources that share the same **Router ID** belong to the same flow router, i.e. a group of alternate sources for the same flow. In the Media Sources table, you can see the Router ID of each source, activate a specific source as the flow router's current input, set its priority, and enable automatic deactivation once it reaches end-of-input so another source can take over. To add a new input as an alternate source to an existing flow router, fill in the router's ID in the **Router ID** field on the "Add URL Input" page.
