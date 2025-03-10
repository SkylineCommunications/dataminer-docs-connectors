---
uid: Connector_help_AMWA_NMOS_IS-04_Registry
---

# AMWA NMOS IS-04 Registry

NMOS is a family name for specifications produced by the Advanced Media Workflow Association related to networked media for professional applications.

## About

Allows control and monitoring applications to find the resources on a network. Resources include Nodes, Devices, Senders, Receivers, Sources, Flows.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Websocket        |              |                   |

### Product Info

| Range     | Supported Firmware                  |
|-----------|-------------------------------------|
| 1.0.0.x   | Supports IS-04 Query API v1.2, v1.3 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     |                       |                         |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

## How to use

Set element configurations. Websockets will be open at runtime.
