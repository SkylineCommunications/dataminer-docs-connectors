---
uid: Connector_help_NBCU_Amagi_Channel_Status_Technical
---

# NBCU Amagi Channel Status

The NBCU Amagi Channel Status connector is designed to retrieve and monitor real-time statuses of Amagi channels, providing an overview of the health state of each channel. It communicates via HTTP requests to fetch and display relevant data, including channel names and agent states.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP Address/Host**: The polling IP or URL of the destination.
- **IP Port**: The IP port of the destination (default: *443*).
- **Device Address**: The bus address of the device. If a proxy server needs to be bypassed, specify *BypassProxy*.

## Usage

### Token Initialization

On the **General** page, you must configure a token obtained from the GUI or vendor. This token is required for authentication and will be used for all requests sent by the connector.

### Channel Status Table

The **Channel Status** table provides real-time insights into monitored channels. The table includes:

- **Channel Name**: The identifier for each channel.
- **Agent State**: The operational state of the channel.

If the Channel Prefix parameter is filled, it will be added to the channel name.
```
Format: {Channel Prefix}_{Channel Name}
```
