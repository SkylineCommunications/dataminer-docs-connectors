---
uid: Connector_help_Qbit_Q820
---

# Qbit Q820

The Qbit Q820 RAVENNA/AES67 audio interface connects up to 16 digital (AES3) audio interfaces with RAVENNA/AES67 IP-audio networks. Incoming audio signals are coded into RAVENNA/AES67 and can then be fed into IP-audio networks over redundant IP interfaces. The audio interface is also equipped with a MADI interface

The connector uses HTTP to poll the Qbit Q820.

## About

### Version Info

| Range              | Key Features          | Based on | System Impact |
|--------------------|-----------------------|----------|---------------|
| 1.0.0.x [SLC Main] | HTTP initial version. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | V2 A5 RC5              |

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
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: Default: *false*.

### Initialization

Log in on the **Login** page with the **Username** and **Password** required to generate the access token and refresh token of the Qbit Q820 device.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

This page displays the Clock, Madi, and Ravenna parameters.

### Channels

On this page, channels are displayed in a table.
