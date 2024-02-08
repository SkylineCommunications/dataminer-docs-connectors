---
uid: Connector_help_Amagi_CLOUDPORT_Playout_Service_Manager
---

# Amagi CLOUDPORT Playout Serivce Manager

This connector is used to monitor and the Amagi CLOUDPORT Playout Service Manager.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   |                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

Once a Token is configure in the driver, this is used for all the requests that the driver sends.

## Initialization

A Token must be configure under the Security page. This is obtained from the GUI or vendor.

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *443*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

You can find all the information you need to monitor the HTTP connection, Feeds on Air and Headends in the General page.