---
uid: Connector_help_Velocix_Origin_Platform
---

# Velocix Origin Platform

Velocix Origin is a cloud-native software-defined storage platform for video streaming that helps video businesses deliver high-quality live, on-demand, and time-shifted video services to every connected screen

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \[SLC Main\] | Initial version  | \-           | \-                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | v2.5.0                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | \-                    | \-                      |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

This connector uses credentials to be able to establish a session to the device.

Credentials need to be provided on the **General** \> **Credentials** page.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

This connector uses a "Poll Manager", which can be found on the Poll Manager page.

The Poll Manager allows you to configure the object or partition polling speeds:

- **Object Name** indicates the partition to be polled
- **Poll State** indicates if the partition polling is enabled or disabled.
- **Poll Frequency** indicates the frequency at which the partition will be polled.
- **Last Polled** indicates the last time an attempt was made to poll this partition.
- **Response State** indicates if the response was successful.
