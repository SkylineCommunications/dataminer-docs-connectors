---
uid: Connector_help_Verimatrix_MDRM_Server_Technical
---

# Verimatrix MDRM Server

## About

Verimatrix MDRM (Multi-DRM) is a cloud-based digital rights management solution that supports multiple DRM systems. 
It enables secure content delivery by managing licenses and entitlements across different platforms and devices.
The protocol integration makes it possible to monitor the service.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP Connection:

- **IP address/host**: The polling IP or URL of the device.

SNMP Settings:

- **IP port**: The IP port of the device, by defualt *161*.
- **Get community string**: The community string used when reading values from the device. (default: *public*)
- **Set community string**: The community string used when setting values on the device. (default: *private*)

## How to use

The element created with this connector provides several data pages for monitoring and management:

- **General**: Displays system information.
- **Interface**: Shows detailed interface statistics, including calculated bitrates.
- **Host Resources**: Presents general host resource metrics and storage information.
- **Processes**: Lists running processes and their status, including error flags and messages.
- **Memory**: Reports on memory usage and availability.
- **Partitions**: Displays disk and partition statistics.
- **Load**: Shows system load averages and related error indicators.

Each page is automatically polled at regular intervals. The connector supports SNMP read and write operations for applicable parameters.