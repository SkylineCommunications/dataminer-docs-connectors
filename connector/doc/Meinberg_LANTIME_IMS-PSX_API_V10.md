---
uid: Connector_help_Meinberg_LANTIME_IMS-PSX_API_V10
---

# Meinberg LANTIME IMS-PSX API V10

The **PSX** (Precision Synchronization eXpert) provides a powerful IEEE1588 PTP solution designed to integrate into 10 Gigabit networks conventionally found in high-bandwidth environments such as data centers, broadcasting & media production, telecom and financial networks.

## About

### Version Info

| Range                | Key Features     | Based On     | System Impact                                                                   |
|----------------------|------------------|--------------|---------------------------------------------------------------------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | Minimum required DataMiner version is **10.2.0.0 - 12603**. |

### Product Info

| Range     | Supported Firmware     | REST API Version     | Supported Types                 |
|-----------|------------------------|----------------------|---------------------------------|
| 1.0.0.x   | 7.08.x       | 17.x.y     | PSX210                          |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | Yes | Yes | DataMiner connector:<br>- [Meinberg LANTIME Modular API V10](xref:Connector_help_Meinberg_LANTIME_Modular_API_V10) | DataMiner connector:<br>- [Meinberg LANTIME IMS-PSX API V10 - PTPv2 Instance](xref:Connector_help_Meinberg_LANTIME_IMS-PSX_API_V10_-_PTPv2_Instance) |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

### Initialization

#### Slot ID

The DataMiner element will not know which slot it needs to represent until the slot ID has been provided.

On the **General** page, the **slot ID** must be configured.

#### REST API

The HTTP communication uses a REST API, which needs to be enabled.

On the device's web interface, make sure the **Enable REST API** option is selected under the **general settings** on the **System** page.

#### HTTP Credentials

The HTTP communication will not be up and running until the necessary HTTP credentials have been provided.

On the **Credentials** page of the element, the **user name** and **password** must be configured.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

REST (Representational State Transfer) calls are used to retrieve the device information.

### HTTP Communication

On the **HTTP Communication** page, you can track the HTTP sessions used for communicating with the device.

This makes it possible to follow the communication flow and provides some useful statistics, e.g. request time, response time, time span (RTT), etc.

- **HTTP Sessions State**: If you enable this setting, the active HTTP sessions will be tracked.
- **HTTP Sessions Max Count**: This determines the maximum number of HTTP sessions that will be tracked.

### Inter App

On the **Inter App** page, an overview is provided that allows you to track the inter application communication and the related handlers.

#### Inter App Communication

Overview of the inter application communication events and messages.

The state of a communication object indicates whether it is waiting to be processed, being processed, executed successfully, or failed.

#### Inter App Handlers

Overview of the inter application handlers of the received events and messages.

Every communication object will be represented by a related handler. The handler is responsible for taking the necessary actions depending on the related communication object.
