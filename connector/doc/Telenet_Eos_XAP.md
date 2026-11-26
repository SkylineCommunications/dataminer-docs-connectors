---
uid: Connector_help_Telenet_Eos_XAP
---

# Telenet Eos XAP

The Telenet Eos XAP protocol provides an interface for integration and management of EOS XAP set-top box devices. It allows remote control, configuration, and monitoring of key parameters such as HDMI resolution, device identifiers, and video stream URLs to optimize functionality and ensure efficient operation.

## About

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

- **IP address/host**: The HTTP gateway host used for XAP requests.
- **IP port**: The gateway port (default: *443*).
- **Device address**: The device address (default: *false*).

## How to Use

The element consists of the data pages detailed below.

### General

The **General** page includes the following parameters:

- **Press Key**: This parameter is used to simulate the pressing of buttons on the remote control. You can select a specific key to trigger an action on the set-top box. It supports discrete measurements, providing a clear response for each action.
- **HDMI Resolution**: Displays or configures the current HDMI output resolution of the set-top box. You can use this to read the current resolution and set a new resolution to adjust the display settings as required.

From connector version 1.0.0.3, the page also includes:

- **Broker Status**: Shows whether the set-top box is connected to its broker. A disconnected or unavailable status triggers a warning by default.
- **Power State**: Shows whether the set-top box is operational or in active standby. Alarm levels can be configured in an alarm template. An unavailable state triggers a warning by default.
- **Auto Standby Timer**: Shows the auto standby timer in seconds.
- **Refresh Status**: Requests an update of the broker status, power state, and auto standby timer.

The status values are also refreshed every 12 hours. When a response is processed, an unsuccessful HTTP status, invalid data, or an unrecognized status is shown as *N/A*.

### Settings

The **Settings** page includes the following parameters:

- **Set-Top Box ID**: A unique identifier for the EOS XAP set-top box. This parameter is essential for differentiating between devices in a multi-device environment.
- **Video Stream URL**: Specifies the URL for the video stream associated with the set-top box. This parameter is critical for defining the source or destination of the video stream and supports both reading and writing operations.
