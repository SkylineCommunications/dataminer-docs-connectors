---
uid: Connector_help_ServiceNow_Authenticator
---

# ServiceNow Authenticator

The ServiceNow Authenticator is a connector used to configure and store the authentication details required to communicate with a ServiceNow instance.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

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

#### HTTP Connection - 1

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

## How to use

To use the connector, first specify the required authentication details such as username, password, client ID, client secret and instance URL.

Once this info has been provided, the connection with a ServiceNow instance can be tested and any integration with this instance can use the stored connection details.
