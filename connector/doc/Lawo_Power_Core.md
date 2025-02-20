---
uid: Connector_help_Lawo_Power_Core
---

# Lawo Power Core

This connector is used to monitor a Lawo Power Core device. This device is a remote production solution for audio consoles with integrated modular I/O, DSP and IP streaming capabilities and uses Ember+ as its communication protocol.

## About

### Version Info

| Range              | Key Features                            | Based on | System Impact |
|--------------------|-----------------------------------------|----------|---------------|
| 1.0.0.x            | Initial version                         | -        | -             |
| 1.0.1.x [SLC Main] | LAWO EmberPlusSharp Library integration | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |
| 1.0.1.x | -                  |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Smart-Serial Main Connection [1.0.0.x Range]

In range 1.0.0.x, this connector uses a smart-serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination (default: *9000*).

#### Virtual Connection [1.0.1.x Range]

In range 1.0.1.x, this connector uses a virtual connection to set up the communication through the official EmberPlusSharp Library from LAWO.

The following parameters need to be configured on the **General** page of the element:

- **IP Address**: The polling IP or URL of the destination.
- **IP Port**: The IP port of the destination (default: *9000*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector sends requests for all parameters it wants to poll and listens to all incoming messages. It then filters and processes the useful messages. This information is then displayed on the appropriate page of the connector. The name of each page indicates which kind of parameters can be found on that page.
