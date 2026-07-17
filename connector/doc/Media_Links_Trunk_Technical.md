---
uid: Connector_help_Media_Links_Trunk_Technical
---

# Media Links Trunk

## About

The Media Links Xscend Trunk module is an interface module that connects a Media Links Xscend chassis to an IP media network. It acts as a high-density gateway, multiplexing signals from various media processing cards and transporting them across the network.

This connector is used to monitor Trunk modules installed in the Xscend chassis.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- IP address/host: The polling IP or URL of the destination.
- IP port: The IP port of the destination.

### Initialization

For the connector to start polling data from the data source, you will need to provide the user name and password credentials. In addition, on the **General** page, you will need to set the slot index of the Trunk module.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

By setting the **Display Alarms** parameter on the **Alarms** page, you can choose to display all alarms or only active alarms.
