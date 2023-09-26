---
uid: Connector_help_Inmarsat_BGAN_IBIS
---

# Inmarsat BGAN IBIS

The Inmarsat BGAN IBIS connector is used to monitor the BGAN network and execute small operations. The BGAN network is a satellite communications network that allows voice, video and data sessions on remote terminals.

## About

### Version Info

| **Range**            | **Key Features**                          | **Based on** | **System Impact** |
|----------------------|-------------------------------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial Version                           | -            | -                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).

### Initialization

The credentials must be filled in on the General page in order for any information to be polled. As long as this is not done, the element will not work. The credentials list is as follows:

- Scope
- Client ID
- Client Secret

The default scope, client ID, and secret can be found in the Rest API documentation. However, they will be configurable in the network.

### Redundancy

There is no redundancy defined.

## How to use (1.0.0.x)

### General

Credentials can be configured on this page, and a login can be enforced. There is also information on the current status of the authentication process.

### Terminal

This page contains a Terminals table as well as buttons to subpages: Position and Messages.

- The **Position** subpage displays the position information of the terminals.
- The **Messages** subpage displays the Latest to Mobile Messages and Latest From Mobile Messages of the Terminals.

### Terminal Tree Control

This page contains a tree control that links the terminal data together.

### Poll Manager

This page contains the Polling Manager table, which manages the polling of the API calls with individual timers. It also shows the time when the API call was last polled.
