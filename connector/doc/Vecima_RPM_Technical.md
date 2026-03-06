---
uid: Connector_help_Vecima_RPM_Technical
---

# Vecima RPM

## About

The Vecima RPM (Remote PHY Manager) connector is designed to monitor and manage Remote PHY devices in DOCSIS networks. It retrieves comprehensive information about PHY cores, RF channels, network status, and hardware components through HTTP-based communication with the Vecima RPM management system.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Bus address**: The bus address of the device (default: *ByPassProxy*).

### Initialization

To establish communication with the RPM device, configure the **Username** and **Password** on the **Configuration** page. Once authenticated, the connector will begin polling information from the managed Remote PHY devices.

## How to use

The element created with this connector provides several data pages for monitoring and management:

- **General**: Displays the number of cores and RPDs.

- **Nodes**: Shows an overview of all managed RPD (Remote PHY Device) nodes.

- **Cores**: Presents detailed information about PHY cores in a table for easy analysis and monitoring.

- **PTP Status**: Displays Precision Time Protocol operational status of all RPDs.

- **Ethernet Links**: Shows the status and statistics of Ethernet connections of all RPDs.

- **US RF Channels**: Lists upstream RF channel information, including frequencies, power levels, channel number...

- **DS RF Channels**: Lists downstream RF channel information, including frequencies, power levels, channel number...

- **SFPs**: Provides detailed information about Small Form-factor Pluggable transceivers of all RPDs.

- **Tunnel Status**: Monitors the status of unicast and multicast tunnels between Remote PHY devices and the CCAP core.

- **Sensors**: Displays different sensors from nodes.

- **RF Amplifiers**: Shows the performance metrics of RF amplifiers in the Remote PHY devices.

- **Configuration**: Allows configuration of connector settings, including the option to enable the debug page for troubleshooting purposes.
