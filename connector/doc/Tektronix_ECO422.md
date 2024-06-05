---
uid: Connector_help_Tektronix_ECO422
---

# Tektronix ECO422

The **Tektronix ECO422** connector is used to display information from another connector, i.e. the Adam Converter connector (which converts I/O to Ethernet).

## About

With this connector, you can view specific information from another connector. This information can easily be adjusted when necessary. Both read-only and editable parameters are available.

### Version Info

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## Usage

### General

This page displays the selected information.

To change the displayed information, use the **Element Connections** app. There, you can link any parameters that support a virtual connection. (These parameters have a virtual option attribute (source/destination) within the Type tag of the protocol). Via drop-down lists, you can change the linked elements and the linked parameter.
