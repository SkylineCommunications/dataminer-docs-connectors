---
uid: Connector_help_Evertz_Magnum_SDVN_Router_Technical
---

# Evertz Magnum SDVN Router

## About

This connector can be used to control the Magnum application. It allows DataMiner to act as any other router panel connected to the Evertz Magnum application.

The connector supports serial-based routing control and HTTP-based retrieval of namesets and salvos. It integrates tightly with the Evertz ecosystem to provide matrix-level routing, crosspoint control, locking, and profile support directly from within the DataMiner environment.

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

#### HTTP Connection

This connection is only used to obtain namesets, labels, profiles, and salvos. The connector can work without this connection enabled, but it still needs to be configured.

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Magnum Configuration

To use this connector, the Magnum application must be configured to expose a virtual router (with x inputs and y outputs) that corresponds to the settings used during the creation of the DataMiner element. The IP and port used in Magnum must match those entered in the element configuration.

## Authentication

Two methods are supported depending on the firmware or Magnum configuration.

### Authorization Code Grant

Used when OAuth2 token-based authentication is enabled.

On the **OAUTH2 Connection Info** page, configure:

- **Client ID**: Provided by the Magnum system administrator.
- **Client Secret**: Provided by the Magnum system administrator.
- **Time to Refresh Token**: Set this to less than the token expiration time to maintain a valid session.

### Client Credentials Grant

Used for simpler integrations. Only the following fields will need to be configured for this (on the **General** page):

- **Username**: REST API Username
- **Password**: REST API Password

Nothing has to be configured on the OAUTH2 page for this method.

## Configuration Parameters

On the **General** page, configure the following parameters:

- **Device**: Targeted device for routing.
- **Breakaway Mode**: Choose between single or quad channel routing.
- **Number of Audio Channels**: Select a number from 0 to 16 (A to P).
- **Operation Mode**: Select Quartz only or Quartz + API.
- **View Nameset**: Determines which nameset is used by default when making crosspoints.
- **Polling Time Type** (for Quartz data only using server time):
  - If set to *Poll by Interval*, the connector will use the value defined under **Poll Data Interval**.
  - If set to *Poll by Time of Day*, the connector will use the schedule defined under **Polling by Time of Day**.
- **Polling Delay on Quartz**: Defines a time interval during which Quartz data will not be polled if a previous polling cycle was completed within that window. This is useful after an element restart to prevent redundant polling cycles, which can take a while.

On the **Quartz** page:

- **Profile ID**: Used to specify the routing profile for crosspoints.

## Pages Overview

- **General**: Main configuration parameters, credentials, polling control, and refresh options.
- **Sources**: Displays the list of sources; allows editing of source notes.
- **Destinations**: Core routing operations; perform crosspoints, lock/unlock destinations.
- **Namesets**: Shows up to five namesets with labels per source/destination.
- **Audit**: Contains crosspoint logs and error messages.
- **Debug**: HTTP response logs, token status, internal flags for troubleshooting.
- **Quartz**: Related to routing via the Quartz interface.
- **OAUTH2 Connection Info**: Used when Authorization Code authentication is enabled.
- **Labels / Profiles / Salvos / Devices**: Available when Operation Mode is set to Quartz + API.

## Notes

The connector is designed to poll all the Quartz data first and then poll data using HTTP (if enabled).

There are three buttons on the General page that allow you to refresh the data of the connector.

- **Quartz Refresh All** will initiate the polling of all data related with this connection's sources, destinations, crosspoint connections, and lock statuses.

- **Quartz Cancel Polling** can be used to stop the Quartz polling phase at any moment if it is currently in progress.

- **HTTP Refresh** will initiate the polling for the REST API part, which includes namesets, salvos, profiles, and labels.
