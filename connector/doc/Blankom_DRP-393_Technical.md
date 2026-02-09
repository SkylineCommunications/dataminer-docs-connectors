---
uid: Connector_help_Blankom_DRP-393_Technical
---

# Blankom DRD-700

## About

The Blankom DRP‑393 is a professional MPEG‑2/MPEG‑4 SD/HD receiver/decoder equipped with ASI input, optional DVB frontends, dual CI slots, extensive VBI capabilities, and optional HD/SD‑SDI output. The DataMiner connector provides centralized monitoring and control of the decoder workflow, input sources, Conditional Access modules, network interfaces, and output configurations.
It gives operators a clear overview of the device’s operational state and decoding chain, helping them safeguard the quality and continuity of delivered services.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP Connection:

- **IP address/host**: The polling IP or URL of the device.

SNMP Settings:

- **IP port**: The IP port of the device, by default *161*.

- **Get community string**: The community string used when reading values from the device (default: *public*).

- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the device.

## How to use

The element created with this connector provides several data pages for monitoring and management:

- **General**: Shows basic device information such as model, firmware version, and main status indicators. Subpages include licenses, messages, and logs. These pages provide detailed information about installed software options, system status messages, and internal logbook entries.

- **System**: Displays device configuration details including time configuration.

- **User Accounts**: Lists all configured users.

- **Network**: Shows control and data port IP settings and SFP module status. The SNMP subpage displays trap receivers and enabled alarm severities.

- **Inputs**: The Inputs page shows monitoring parameters for all supported input modes. Depending on the active source (ASI, IP, DVB‑S/S2, DVB‑T/T2, DVB‑C), the page displays the relevant and general parameters.

- **Conditional Access**: This page provides an overview of the conditional access status for both CI slots, the configured BISS settings, and a transport stream services table showing which services are encrypted and how they are processed by the device.

- **Decoder**: The decoder page provides visibility into the active decoding chain of the DRP‑393 and allows configuration of the decoding parameters.

- **Outputs**: This page provides an overview of the configured MPTS and SPTS output settings, including their destinations, protocols, and routing behavior, while subpages list the services carried in each output stream.

- **Service Filtering**: Shows the configured filtering mode and the resulting input/output data rates. The subpage lists all services and their filtering state, allowing operators to validate how the DRP‑393 manages service reduction or pass-through for IP/ASI output.

Each page is automatically polled at regular intervals. The connector supports SNMP read and write operations for applicable parameters.
