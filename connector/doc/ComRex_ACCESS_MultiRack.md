---
uid: Connector_help_ComRex_ACCESS_MultiRack
---

# ComRex ACCESS MultiRack

ACCESS MultiRack is a rackmount IP audio multi-codec, capable of establishing and managing up to five simultaneous full-duplex IP audio codec connections. It is used for the encoding and decoding of audio data over an IP network and makes real-time audio communication between multiple locations easier.

## About

### Version Info

| Range     | Key Features     | Based on     | System Impact     |
|-----------|------------------|--------------|-------------------|
| 1.0.0.x   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### WebSocket Connections

This connector uses 5 simultaneous WebSocket connections and requires the following input during element creation:

WEBSOCKET CONNECTION:

- **IP address/host**: The polling IP of the device, for each of the 5 WebSocket connections.
- **IP port**: The IP port of the device. Required. Range: *81-85*. Default value: *81*.

### Initialization

Once the element has been created in DataMiner, the **Login** page allows you to specify the password to log in to the device (if the WebSocket connection is open).

After you click the **Login** button, the **Login Status** will indicate whether the login was successful.

## How to Use

The element has following data pages:

- **General**: Displays general information about the device.

  The **Login** subpage contains the WebSocket status information, the Password box and Login button, and login status information.

- **License Manager**: Shows a list of all the licenses on the device.

- **Instance Settings**: Shows instance-specific settings.

- **Network Manager**: Shows device-wide network settings.

- **Global Settings**: Shows device-wide settings, such as NTP, AE67, etc.

- **Overview**: Shows a tree view with all the instances and their connections, profiles, and channels.

- **Connections**: Displays the Peers Table. With the right-click menu of the table, you can connect, disconnect, add, edit, or delete a peer.

- **Profiles**: Contains the Profiles Table.

- **Channels**: Displays channels and channel options.

## Notes

If a WebSocket connection is lost, the status on the Login subpage will show the connection as *Closed*. To reconnect, click the **Reconnect** button on the Login subpage.
