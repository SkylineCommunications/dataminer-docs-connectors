---
uid: Connector_help_Fraunhofer_DAB_Content_Server
---

# Fraunhofer DAB Content Server

The Fraunhofer DAB ContentServer is a flexible and highly reliable professional broadcasting solution developed for the digital radio standard DAB (Digital Audio Broadcasting).

It combines internal audio encoding, support for remote audio encoders, multimedia data management and multiplex generation. A convenient and user-friendly web interface enables configuration and system monitoring via remote access (ContentServer-as-a-Service concept).

The Fraunhofer DAB ContentServer is a complete headend system possessing triple functionality:
  - Internal audio encoding and support for remote audio encoders
  - Multimedia DataServer  
  - DAB Ensemble/Service Multiplex Generator

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

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *443*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *byPassProxy*.]

### Initialization

No extra configuration is needed.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

On the **General** page, you can find the overall status parameters for the contribution, content server and distrubution as well as the on-air multiplex. The page also contains some system actions such as:
  - Restart The Transmission
  - Stop The Transmission
  - Halt the Content Server
  - Clear SMART (restart monitor of connected drives)
  - Gratuitous ARP (rediscover new IP on the network)
  - Restart the Audio Encoders

The **System Status** page contains the complete status overview of all items.
The **Contribution**, **Content Server** and **Distribution** pages are a filtered set of the System Status table.