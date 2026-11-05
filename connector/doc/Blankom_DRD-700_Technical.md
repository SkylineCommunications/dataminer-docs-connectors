---
uid: Connector_help_Blankom_DRD-700_Technical
---

# Blankom DRD-700

## About

The Blankom DRD-700 is a professional Quad Multistream Processor supporting ASI, IP, DVB‑S/S2, DVB‑T/T2, DVB‑C, and CI-based descrambling. The connector integration provides centralized monitoring of all transport stream inputs, outputs, CAM modules, system resources, and network interfaces. It enables operators to quickly detect faults, validate stream configurations, and manage services.

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

- **User Accounts**: Lists all configured users and their access levels.

- **Network**: Shows control and data port IP settings and SFP module status. The SNMP subpage displays trap receivers and enabled alarm severities.

- **Inputs TS**: Shows the active input source (ASI, IP, DVB) and the present services for TS1–TS4.

- **Inputs DVB‑S**: Displays information about the input DVB‑S/S2 and makes it possible to tune parameters specific to satellite input.

- **Inputs DVB‑T**: Displays information about the input DVB‑T/T2 and makes it possible to tune parameters specific to terrestrial input.

- **Inputs DVB‑C**: Displays information about the input DVB‑C and makes it possible to tune parameters specific to cable input.

- **Inputs IP**: Shows IP input configuration parameters.

- **Common Interface**: Displays information about encrypted services and their associated conditional access parameters, including the active CA sources and service lists per slot.

- **Outputs IP**: Shows the configuration of IP-based outputs, including MPTS and SPTS destinations, protocols, and multicast settings. Subpages list the services carried in each output stream.

- **Outputs ASI**: Displays ASI output routing and assigned transport streams across all output ports. Subpages provide an overview of the services included in each ASI output.

Each page is automatically polled at regular intervals. The connector supports SNMP read and write operations for applicable parameters.
