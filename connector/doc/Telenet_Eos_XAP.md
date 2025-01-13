---
uid: Connector_help_Telenet_Eos_XAP
---

# Telenet Eos XAP

The Telenet Eos XAP protocol provides an interface for integration and management of EOS XAP set-top box devices. It allows for remote control, configuration, and monitoring of key parameters such as HDMI resolution, device identifiers, and video stream URLs to optimize functionality and ensure efficient operation.
## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 5.3.5                  |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device, e.g. xxx.yyy.zzz.com.
- **IP port**: The IP port of the device, e.g. 8080.
- **Device address**: The device address (default: ByPassProxy).

## How to use

The element consists of the data pages detailed below.

### General

The **General** page includes the following parameters:

- **Press Key**: This parameter is used to simulate the pressing of buttons on the remote control. You can select a specific key to trigger an action on the set-top box. It supports discrete measurements, providing a clear response for each action.
- **HDMI Resolution**: Displays or configures the current HDMI output resolution of the set-top box. It allows reading the current resolution and setting a new resolution to adjust the display settings as required.


### Settings

The **Settings** page includes the following parameters:

- **Set-Top Box ID**: A unique identifier for the EOS XAP set-top box. This parameter is essential for differentiating between devices in a multi-device environment.
- **Video Stream URL**: Specifies the URL for the video stream associated with the set-top box. This parameter is critical for defining the source or destination of the video stream and supports both reading and writing operations.
