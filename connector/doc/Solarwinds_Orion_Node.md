---
uid: Connector_help_Solarwinds_Orion_Node
---

# Solarwinds Orion Node

The **Solarwinds Orion Node** is part of the **Solarwinds Orion** protocol. This connector is intended to present information related to a specific node on the network.

## About

A REST/JSON API will be used to define queries sent to the tool through HTTP POST commands.

This connector is automatically generated by the connector **Solarwinds Orion**, range 1.0.0.1.

The element is generated when **DVE Creation** is enabled on the **Orion Nodes** table of the **Solarwinds Orion** element.

For more information about the API, refer to the website <https://github.com/solarwinds/OrionSDK/wiki>. For more information about the Orion suite, refer to <http://www.solarwinds.com/>.

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | NPM 10.4                    |

## Installation and configuration

### Creation

HTTP main connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: *17778*
- **Bus address**: *bypassproxy*

## Usage

### Node

This page contains general information about the node.

### Node Status

This page shows the current statistics and measurements for the node.

### Interfaces

This page contains information related to the interfaces allocated to this specific node.

### Volumes

This page displays information about the volumes that are being used by this node.
