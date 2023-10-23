---
uid: Connector_help_Inmarsat_BGAN_IBIS
---

# Inmarsat BGAN IBIS

The Inmarsat BGAN IBIS connector is used to monitor the BGAN network and execute small operations. The BGAN network is a satellite communication network that allows voice, video, and data sessions on remote terminals.

## About

### Version Info

| Range              | Key Features    | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

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

To make sure the connector can retrieve information, fill in the credentials on the **General** page:

- Scope
- Client ID
- Client Secret

The default scope, client ID, and secret can be found in the Rest API documentation. However, they will be configurable in the network.

## How to use (1.0.0.x)

### General

On this page, you can configure credentials (see [Initialization](#initialization)) and enforce a login. You can also check information on the current status of the authentication process.

### Terminal

This page contains a Terminals table as well as buttons to the Position and Messages subpages.

- The **Position** subpage displays the position information of the terminals.
- The **Messages** subpage displays the Latest to Mobile Messages and Latest From Mobile Messages of the terminals.

### Terminal Tree Control

This page contains a tree control that links the terminal data together.

### Poll Manager

This page contains the Polling Manager table, which manages the polling of the API calls with individual timers. It also shows the time when the API call was last polled.
