---
uid: Connector_help_Dell_PowerVault_ME5024
---

# Dell PowerVault ME5024

The Dell EMC PowerVault ME5024 is a high-performance storage array designed for small to medium-sized businesses and remote offices. It supports a variety of drive types (SSD and HDD) and multiple connectivity options (Fibre Channel and iSCSI).

## About

### Version Info

| Range              | Key Features                               | Based on | System Impact |
|--------------------|--------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. Only includes monitoring. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

#### HTTP Secondary Connection

In case the main connection goes down, the connector can poll using the backup connection, which is configured in the same way as the main connection.

### Initialization

The element communicates with the data source using the **REST API**. In order enable this communication, you need to fill in the **HTTP Username** and **HTTP Password** parameters on the **General** page.

### Redundancy

There is API polling redundancy, which triggers when a 200 OK is not returned by the device.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

When the credentials have been specified as detailed above under "Initialization", the element will execute a GET request using these credentials. If they are correct, the element will receive a token from the data source so that it can remain logged in and continue to execute calls to update the parameters of the connector, including system, host names, disks, fans, and power supplies info.

## Notes

For now, this connector also supports the Dell PowerVault ME4024.
