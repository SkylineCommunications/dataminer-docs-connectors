---
uid: Connector_help_Viaplay_SCTE_Injector
---

# Viaplay SCTE Injector

Viaplay SCTE Injector is a connector designed to facilitate the manual injection of SCTE 35 messages into live streams.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | N/A                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Serial connection

This connector uses a serial connection, and requires the following input during element creation.

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: You can enter an arbitrary IP address, because it will be overwritten when the element is started. You will be able to select a device, and the IP address will then be dynamically updated.
  - **IP port**: You an enter an arbitrary port, because it will be overwritten when element is started. You will be able to select a device, and the port will then be dynamically updated.

## How to use

### General

This page displays basic information about the available devices, including the device name, IP address, and port.

### Management

In the Management table on this page, you can select a device and set the duration of an interruption. Use the **Take** button in the table to send an interruption command, or use the **Stop** button to halt the interruption or to stop an interruption if it started by mistake.

The timestamp of the last use of the Take command is also displayed.
