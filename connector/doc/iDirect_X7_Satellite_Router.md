---
uid: Connector_help_iDirect_X7_Satellite_Router
---

# iDirect X7 Satellite Router

The iDirect X7 Satellite Router is a multi-core hardware system that enables service providers to deliver the data rates needed for bandwidth-heavy business applications and multicast services like IP TV, distance learning, HD broadcast, digital signage and video. It features a compact, rack-mount design, embedded 8-port switch, a 2nd DVB-S2 demodulator, variant power supply configurations, making it suitable for voice and data services that simultaneously receive multicast channels over the same or over a second transponder or satellite - even when spot-beam HTS capacity is combined with Ku and C-band capacity.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [SLC Main] | - A Telnet connection is established with the product through serial communication in order to retrieve system information.<br>- An HTTP connection is used to retrieve modem status information. | - | - |

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

#### Serial Telnet Connection Connection

This connector uses a serial connection to execute Telnet commands and requires the following input during element creation:

SERIAL CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *23*).

## Usage

### General

This page displays **system information** parameters for the **Modem equipment**.

It also contains a subpage to configure the **Credentials**, which must be configured in order to poll data from the referred product

### Modem Status

This page displays **metrics** and **states** concerning the **Transmitter** and the **Receiver** components of the product.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.
