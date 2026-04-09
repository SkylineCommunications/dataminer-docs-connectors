---
uid: Connector_help_AvL_Technologies_Intelligent_Terminal_Controller_Explorer_Technical
---

# AvL Technologies Intelligent Terminal Controller Explorer

## About

The AvL Technologies Intelligent Terminal Controller (ITC) Explorer is a control system designed for satellite communication antennas. It manages antenna positioning, signal acquisition, and RF chain components such as receivers and modems. The device provides real-time telemetry, fault monitoring, and system diagnostics through a web-based interface and WebSocket communication, enabling precise control and reliable operation of satellite terminals in both fixed and mobile environments.
This connector integrates the AvL Technologies Intelligent Terminal Controller (ITC) Explorer into DataMiner using an HTTP connection with WebSocket-based communication for real-time data exchange.

## Configuration

### Connections

#### HTTP Connection – ITC Explorer

This connector uses an HTTP connection combined with WebSocket communication and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The IP address or hostname of the ITC Explorer device.
- **IP port**: The port used by the web interface (typically 80 or 443).
- **Bus address**: Not required.

### Initialization

After element creation:

- Configure authentication credentials (username and password).
- Verify that the WebSocket connection status is established.
- Ensure the device is reachable and responding.

### Web Interface

The web interface is only accessible when the client machine has network access to the device.

### How to Use

The connector organizes data across multiple pages:

#### General Page

Provides high-level system and antenna information:

- Active Signal Source
- Antenna Name
- Bandwidth Units
- Core Version
- Effective Isotropic Radiated Power (EIRP)
- Maximum Spectral Density
- Gain-to-Noise Ratio (G/T)
- Local Oscillator Frequency
- Reflector Size
- Azimuth, Elevation, Polarization
- BUC Transmit Frequency
- BUC Temperature
- Position

#### Authentication Page

Handles connection and login status:

- Username
- Password
- Login Status
- WebSocket Status

#### Alarms Page

Displays system faults and warnings:

- Fault Summary
- Warning Summary
- Detailed reasons for:
  - Azimuth motor
  - Elevation motor
  - Polarization motor
  - Transmit modules

#### Receiver Page

Monitors multiple receiver types:

- AVL Receiver:
  - Fault status and reason
  - Lock status
  - Frequency
  - Signal strength

- Virtual Receiver:
  - Lock status
  - Frequency
  - Signal strength

- Power Receiver:
  - Fault status
  - Lock status
  - Frequency
  - Signal strength

#### Modems Page

Provides modem-related information:

- Power Modem:
  - Fault status
  - Lock status
  - Signal strength
  - Frequency
  - Manufacturer
  - Model
  - Serial number
  - Software revision

- Direct Modem:
  - Fault status
  - Lock status
  - Frequency
  - Signal strength
  - Manufacturer
  - Model

#### License Information

Displays license status and version details for:

- AHRS
- Geo acquisition
- Generic motors
- O3b
- Peaking methods
- TLE package
- Web server
- Power receiver
- AVL receiver

## Notes

- Communication relies on WebSockets for real-time updates; loss of WebSocket connectivity impacts data freshness.
- Authentication must be valid for successful data retrieval.
- Some parameters depend on active hardware modules and may not be available in all configurations.
