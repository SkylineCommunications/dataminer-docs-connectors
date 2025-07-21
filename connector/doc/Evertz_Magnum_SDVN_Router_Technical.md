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

Two methods are supported depending on the firmware or Magnum configuration:

### Authorization Code Grant
Used when OAuth2 token-based authentication is enabled.

In the **OAUTH2 Connection Info** page, configure:

- **Client ID**: Provided by Magnum system administrator.
- **Client Secret**: Provided by Magnum system administrator.
- **Time to Refresh Token**: Set this to less than the token expiration time to maintain a valid session.

### Client Credentials Grant
Used for simpler integrations. Only the following fields are required (configured under the **General** page):

- **Username**: REST API Username
- **Password**: REST API Password

No fields in the OAUTH2 page are required for this method.

## Configuration Parameters

On the **General** page, configure:

- **Device**: Targeted device for routing.
- **Breakaway Mode**: Choose between Single or Quad channel routing.
- **Number of Audio Channels**: Select from 0 to 16 (A to P).
- **Operation Mode**: Select Quartz only or Quartz + API.
- **View Nameset**: Determines which nameset is used by default when making crosspoints.
- **Polling Time Type** (for Quartz data only using server time):
    - If set to Poll by Interval, the connector will use the value defined under **Poll Data Interval**.
    - If set to Poll by Time of Day, it will use the schedule defined under **Polling by Time of Day**.
- **Polling Delay on Quartz** Defines a time interval during which Quartz data will not be polled if a previous polling cycle was completed within that window. This is useful after an element restart to prevent redundant polling cycles which can take a while.

On the **Quartz** page:

- **Profile ID**: Used to specify routing profile for crosspoints.

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
The driver is designed to poll all the Quartz data first and then data using HTTP (If enabled)

There are three buttons in the General page which allows the user to refresh the data of the connector.

1) Quartz Refresh All will initialte the polling of all data related with this connection Sources, Destinations names Crosspoint connections, and Lock Statuses. 

2) Quartz Cancel Polling can be use to stop at any moment the Quartz polling phase if currently in progress.

3) HTTP Refresh will initiate the polling for the REST API part which includes Namesets, Salvos, Profiles, and Labels.