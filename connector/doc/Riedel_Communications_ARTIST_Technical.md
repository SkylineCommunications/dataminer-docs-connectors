---
uid: Connector_help_Riedel_Communications_ARTIST_Technical
---

# Riedel Communications ARTIST

The **Riedel Communications ARTIST** connector can be used to poll and configure the data from a Riedel system.

## About

### Version Info

| Range | Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [SLC Main] | - Ports<br/>- Virtual Ports<br/>- Keys<br/>- Virtual Keys<br/>- Conferences<br/>- Groups<br/>- Functions | - | - |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 8.8.RR1            |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection - Primary

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *8193*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

#### HTTP Connection - Secondary

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *8193*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

#### Smart-Serial Connection - Server

This connector uses a serial connection and requires the following input during element creation:

SMART-SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination. Must be set to *any*.
  - **IP port**: The IP port of the destination (default: *8194*).

### Redundancy

Most Riedel ARTIST systems consist of both a primary and a secondary server. At any point in time, only one of these servers will act as the "online" server. While a connection can always be made to both servers, the Riedel ARTIST's information should be retrieved from the "online" server to guarantee the most updated information.

For this purpose, while configuring the DataMiner element, make sure to provide the info of the primary and secondary server for the HTTP connections, respectively. The connector will automatically and continuously detect which server is acting as the "online" server so that all communication can be pointed towards the "online" server at all times.

In case your Riedel ARTIST system does not consist of a failover pair, provide the information of your server for both the primary and the secondary HTTP connection.

## How to use

The Riedel ARTIST system comes with many types of information and data that can be provisioned (create, update and delete). To make the provisioning as user-friendly and straightforward possible, the configuration of these data types is available via designated right-click menus, which are documented in detail below.

### Ports

The following options are available in the right-click menu for the **Ports** table:

- **Create Virtual Key**: Create a virtual key for the selected port.
- **Refresh**: Refresh the selected port's information.
- **Refresh Keys**: Refresh the selected port's key information.
- **Refresh functions**: Refresh the selected port's function information.
- **Call to Conference**: Create a call-to-conference virtual function for the selected port with the provided settings (e.g. virtual function type, conference name, priority, talk and listen privileges, etc.).
- **Call to Group**: Create a call-to-group virtual function for the selected port with the provided settings (e.g. virtual function type, group name, priority, etc.).
- **Call to Port (Local)**: Create a local call-to-port function for the selected port with the provided settings (e.g. virtual function type, port name, priority, etc.).
- **Call to Port (Trunking)**: Create a trunking call-to-port function for the selected port with the provided settings (e.g. virtual function type, port name, priority, etc.).

### Keys

The following options are available in the right-click menu for the **Keys** table:

- **Edit**: Edit the selected key (e.g. label, key mode, latching timeout, etc.).
- **Call to Conference**: Create a call-to-conference function for the selected key with the provided settings (e.g. conference name, priority, talk and listen privileges, etc.).
- **Call to Group**: Create a call-to-group function for the selected key with the provided settings (e.g. group name, priority, etc.).
- **Call to Port (Local)**: Create a local call-to-port function for the selected key with the provided settings (e.g. port name, priority, etc.).
- **Call to Port (Trunking)**: Create a trunking call-to-port function for the selected key with the provided settings (e.g. port name, priority, etc.).
- **Delete All functions**: Deletes all functions related to the selected key.

### Virtual Keys

The following options are available in the right-click menu for the **Virtual Keys** table:

- **Edit**: Edit the selected virtual key (e.g. key mode, latching timeout, etc.).
- **Delete**: Delete the selected virtual key.
- **Call to Conference**: Create a call-to-conference function for the selected virtual key with the provided settings (e.g. conference name, priority, talk and listen privileges, etc.).
- **Call to Group**: Create a call-to-group function for the selected virtual key with the provided settings (e.g. group name, priority, etc.).
- **Call to Port (Local)**: Create a local call-to-port function for the selected virtual key with the provided settings (e.g. port name, priority, etc.).
- **Call to Port (Trunking)**: Create a trunking call-to-port function for the selected virtual key with the provided settings (e.g. port name, priority, etc.).
- **Delete All functions**: Deletes all functions related to the selected virtual key.

### Conferences

The following options are available in the right-click menu for the **Conferences** table:

- **Create**: Create a conference with the provided settings (e.g. name, label, alias, etc.).
- **Edit**: Edit the selected conference (e.g. name, label, alias, etc.).
- **Delete**: Delete the selected conference.
- **Refresh**: Refresh the selected conference's information.

### Groups

The following options are available in the right-click menu for the **Groups** table:

- **Create**: Create a group with the provided settings (e.g. name, label, etc.).
- **Edit**: Edit the selected group (e.g. name, label, etc.).
- **Delete**: Delete the selected group.
- **Refresh**: Refresh the selected group's information.

### Functions

The following options are available in the right-click menu for the **Functions** table:

- **Delete**: Delete the selected function.

The following options are available in the right-click menu for the **Call to Conference Functions** table:

- **Edit**: Edit the selected call-to-conference function (e.g. priority, talk and listen privileges, etc.).
- **Delete**: Delete the selected call-to-conference function.

The following options are available in the right-click menu for the **Call to Group Functions** table:

- **Edit**: Edit the selected call-to-group function (e.g. priority, etc.).
- **Delete**: Delete the selected call-to-group function.

The following options are available in the right-click menu for the **Call to Port Functions** table:

- **Delete**: Delete the selected call-to-port function.

### Notifications

A Riedel ARTIST system also comes with the feature of actively sending smart-serial informational messages to provide updates on changes in the Riedel system.

The type of notifications for which you wish to receive these informational messages can be configured under the **Notification - Registration** page.

Additionally, you can configure how to clean up these received notifications by choosing to keep notifications based either on a **maximum number** or on **maximum age**.
