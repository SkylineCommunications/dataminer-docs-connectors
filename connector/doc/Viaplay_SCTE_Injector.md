---
uid: Connector_help_Viaplay_SCTE_Injector
---

# Viaplay SCTE Injector

Viaplay SCTE Injector is a driver designed to facilitate the manual injection of SCTE 35 messages into live streams. 

## About

### Version Info

| Range            | Key Features | Based on | System Impact |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version. | -           | -                |

### Product Info

| Range | Supported Firmware |
|-----------|------------------------|
| 1.0.0.x   | N/A                     |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                    | -                      |

## Configuration

### Connections

#### Serial connection 

This connector uses a serial connection, and the IP address and port are selected by the user when choosing the device to control.

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**:  Selected by the user from the available devices.
  - **IP port**: Selected by the user from the available devices.
  - **Bus address**: Not required.

## How to use

In the sections below, you can find more information on the data pages of the element and how to use them. 

### General

This page displays basic information about the available devices, including the device name, IP address, and port.

### Management

On this page, there is a Management table to select a device and set the duration of the interruption. The table also includes buttons: **Take** to send the interruption command and **Stop** to halt the interruption or if it started by mistake. Additionally, there is a timestamp of the last use of the Take command
