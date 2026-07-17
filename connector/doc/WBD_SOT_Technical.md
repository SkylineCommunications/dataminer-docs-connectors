---
uid: Connector_help_WBD_SOT_Technical
---

# WBD SOT

## About

The WBD SOT (Source of Truth) is Warner Bros. Discovery's central registry of network entries, keeping track of authoritative source information such as addressing and protection/redundancy details for the streams and devices used across their infrastructure.

This WBD SOT connector interacts with the WBD SOT API to synchronize this registry into DataMiner, giving operators a real-time, consolidated view of all registered entries.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The WBD SOT API endpoint.
- **IP port**: The IP port of the destination.
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

Any credentials required to authenticate against the WBD SOT API (e.g., an API key or token) should be configured on this HTTP connection as well.

### Initialization

On startup, the connector performs the following actions in sequence:

1. **Get API Metadata**: Retrieves application, environment, and API/major version information from the WBD SOT.
2. **Get Connection Status**: Verifies that the WBD SOT API is reachable and ready.
3. **Get Full Sync**: Retrieves the complete list of entries and populates the Entries table.

Once the initial full sync has completed, the connector switches to incremental synchronization (see [Sync from Cursor](#polling-configuration)) to keep the Entries table up to date.

## How to use

Below, you can find more detailed information about the various data pages available in the element.

### General

This page shows metadata about the WBD SOT connection and the API itself, including:

- **Application**, **Environment**, and **App Version**: Identify the WBD SOT application instance the connector is connected to.
- **API Version** and **Current Major**: Indicate the version of the API being used.
- **Connection Status**: Shows whether the connection to the WBD SOT API is currently healthy.

### Entries

This page lists all entries retrieved from the WBD SOT, including:

- **ID** and **Name**: Uniquely identify the entry.
- **Protection**: The protection/redundancy scheme configured for the entry.
- **Address 1**, **SSM 1**, **Port 1**: The primary addressing information for the entry.
- **Address 2**, **SSM 2**, **Port 2**: The backup addressing information for the entry, if configured.
- **Created At** and **Updated At**: Timestamps indicating when the entry was created and last modified in the WBD SOT.

This table is first populated via a full synchronization and is subsequently kept up to date through incremental (cursor-based) synchronization.

### Polling Configuration

On this page, you can control the polling behavior of each underlying API call (Get Metadata, Get Connection Status, Get Full Sync, Get Sync from Cursor):

- **Status**: Enable or disable polling for the API call.
- **Frequency**: Set the polling interval for the API call.
- **Last HTTP Status** and **Last Response**: Show the outcome of the most recent request.
- **Last Poll Time**: Shows when the API call was last executed.
- **Manual Refresh**: Trigger an immediate, out-of-cycle execution of the API call.
- **Execution Counter** and **Error Counter**: Track the number of executions and failures for the API call.

Set an appropriate polling frequency for **Get Sync from Cursor**, as this determines how quickly changes in the WBD SOT are reflected in the Entries table.

### Debug

This page exposes low-level diagnostic information, such as the current sync cursor number and the total number of entries, to help troubleshoot synchronization issues.
