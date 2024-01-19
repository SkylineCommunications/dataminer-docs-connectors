---
uid: Connector_help_2WCOM_IP-8e
---

# 2WCOM IP-8e

The 2WCOM IP-8e is a point-to-point or point-to-multipoint audio encoder using IP-based audio network technologies for real-time streaming.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | Initial version. | - | - |
| 1.0.1.x \[Obsolete\] | - DataMiner Connectivity Framework (DCF) integration added. <br>- Redundant polling added. | 1.0.0.1 | - DCF can cause an additional load on the system. <br>- Existing elements need to be reconfigured to use the redundant connection. |
| 2.0.0.x \[Main range\] | - Conversion of driver from SNMP to HTTP connection. | 1.0.1.1      | \- Existing elements need to be reconfigured to use HTTP conection instead of SNMP. |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.11.12                |
| 1.0.1.x \[Obsolete\]   | 2.11.12                |
| 2.0.0.x   | 2.14.1                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x \[Obsolete\]| Yes                 | Yes                     | -                     | -                       |
| 2.0.0.x   | Yes                 | Yes                     | -                     | -                       |

## Configuration

### Connections

This connector uses HTTP connections and requires the inputs detailed below during element creation.

### HTTP Connection - Primary

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: 80).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### HTTP Connection - Secondary

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: 80).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

### Redundancy

The element is configured with a redundant connection. When the primary connection is no longer responding (i.e. a timeout occurs on this connection), DataMiner will automatically switch to the secondary connection (and vice versa).

## How to use

This connector uses HTTP parameters to access and modify the device parameters.

The connector uses a UI structure similar to the web interface of the device. You can also control the parameters in a similar way.

User needs to log in on the *Login* page using the same credentials as the web interface

To add new multiplexers, you will need to use the web interface of the device (available on a page of the element). These will then be accessible only through the web interface of the device.

The connector does not provide access to sensitive information such as the User, Storage, or Log pages of the web interface.
