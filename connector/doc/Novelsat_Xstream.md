---
uid: Connector_help_Novelsat_Xstream
---

# Novelsat Xstream

The NOVELSAT Xstream multi-purpose gateway is typically used in satellite networks requiring any-to-any high-speed connectivity. It can be used for multiple applications including video delivery, Earth observation, SIGINT, Cloud, and IoT.

This connector retrieves the data from the demodulator and modulator cards from the chassis.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 2.1.2              |

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
- **IP port**: The IP port of the destination (default: *8443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

On the **Settings** page, fill in a token of an admin account. The connector will then retrieve the demodulator and modulator info through the REST API

## How to use

On the **General** page, you can find chassis metrics and a table with connected modules.

For the demodulator and modulator, there are two pages: one for the configuration parameters and one for the status parameters. Each page contains tables displaying the available parameters similar to the web interface of the device.
