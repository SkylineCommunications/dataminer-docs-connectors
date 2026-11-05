---
uid: Connector_help_Ateme_Titan_Edge
---

# Ateme Titan Edge

## About

The Ateme Titan Edge device is an advanced media platform that can have multiple modules like encoders, decoders and gateways.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element created with this connector has the following data pages:

- **General**: Displays general information about the device and lists the current **modules** connected to the device in a table.
- **Alarms**: Lists the current **Active Alarms** on the device.
- **Alarms and Events**: Displays information about alarms and events.
- **DVE**: Allows you to check the DVE configuration and status for the supported modules.
- **Power Supply Units**: Displays information about power supply units.
- **CPU**: Displays information about CPU usage.
- **Ethernet**: Displays information about Ethernet interfaces.
- **Network**: Displays information about network configuration and status.
- **Firewall**: Displays information about firewall status.
- **VPN**: Displays information about VPN connections.
- **Decoder**: Displays the decoder information.
- **Encoder**: Displays the encoder information.
- **Gateway**: Displays the gateway information.
- **SRM Resources**: Displays information about SRM resources.
- **BISS**: Displays and manages BISS services.

### BISS Page

The BISS Services table on the BISS page supports both encoders and decoders. With this table, you can configure and monitor BISS services.

Important notes:

- Descrambling mode is not supported for encoders.
- Entitlement key name is not supported for encoders.
- Entitlement session ID is not supported for decoders.
