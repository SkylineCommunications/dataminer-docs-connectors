---
uid: Connector_help_Fraunhofer_DAB_Content_Server
---

# Fraunhofer DAB Content Server

The Fraunhofer DAB Content Server is a flexible and highly reliable professional broadcasting solution developed for the digital radio standard DAB (Digital Audio Broadcasting).

It combines internal audio encoding, support for remote audio encoders, multimedia data management, and multiplex generation. The web interface allows configuration and system monitoring via remote access (ContentServer-as-a-Service concept).

The Fraunhofer DAB Content Server is a complete headend system with triple functionality:

- Internal audio encoding and support for remote audio encoders
- Multimedia data server
- DAB ensemble/service multiplex generator

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]|Initial version         |-         |-         |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 7.4.14.44065.2023-04-25|

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |-   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *byPassProxy*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

On the **General** page, you can find the overall status parameters for the contribution, content server, and distribution, as well as the on-air multiplex. The page also contains some system actions such as:

- Restart the transmission
- Stop the transmission
- Halt the content server
- Clear SMART (restart monitor of connected drives)
- Gratuitous ARP (rediscover new IPs in the network)
- Restart the audio encoders

The **System Status** page contains the complete status overview of all items.

The **Contribution**, **Content Server**, and **Distribution** pages contain a filtered set of the System Status table.
