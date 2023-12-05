---
uid: Connector_help_Meinberg_microSync
---

# Meinberg microSync

The **microSync** models offer a selection of output signals such as 1 PPS, 10 MHz, IRIG timecodes, programmable pulses, and fiber-optic signals. The network ports enable network synchronization of **NTP** clients and **PTP** slaves.

The microSync product family features the built-in embedded network processor with the sync-optimized meinbergOS firmware. It supports NTP as well as the most common PTP **IEEE 1588** profiles and numerous network protocols for management and monitoring tasks.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 2022.05.6-rc3-u    |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

The HTTP communication will not be up and running until the necessary **HTTP credentials** have been provided.

On the **Credentials** page of the element, the **user name** and **password** must be configured.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

REST (Representational State Transfer) calls are used to retrieve the device information.

### HTTP Communication

On the **HTTP Communication** page, you can track the HTTP sessions used for communication with the device.

This makes it possible to follow the communication flow and provides some useful statistics, e.g. request time, response time, time span (RTT), etc.

- **HTTP Sessions State**: If you enable this setting, the active HTTP sessions will be tracked.
- **HTTP Sessions Max Count**: This determines the maximum number of HTTP sessions that will be tracked.
