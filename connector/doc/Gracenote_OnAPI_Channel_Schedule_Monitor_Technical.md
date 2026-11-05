---
uid: Connector_help_Gracenote_OnAPI_Channel_Schedule_Monitor_Technical
description: "Learn how to configure the Gracenote OnAPI Channel Schedule Monitor connector in DataMiner, including its HTTP connection, API key, and Gracenote ID."
---

# Gracenote OnAPI Channel Schedule Monitor

This is a limited SRM-project-specific connector for DataMiner. It enables monitoring and retrieval of channel schedule data from the Gracenote OnAPI service, supporting streamlined integration and visibility for broadcast and media operations.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: `http://on-api.gracenote.com`.
- **Port number**: The port of the connected device, by default *443*.
- **Timeout of a single command**: Default value: *10000* ms.

## How to Use

This connector uses HTTP requests to populate tables and parameters within the element.

When you have created the element, configure the following parameters to ensure that the connector can retrieve data:

- **API Key**: Specify your key. If you do not have a key yet, contact your Gracenote representative for your API Key Account.
- **Gracenote ID**: Specify your ID provided by your Gracenote representative.
