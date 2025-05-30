---
uid: Connector_help_Rohde_Schwarz_Nx8000_Technical
---

# Rohde Schwarz Nx8000

## About

The Rohde & Schwarz Nx8000 transmitter system offers advanced broadcast transmission with support for multiple standards such as DVB-T/T2, ISDB-T, and ATSC. It provides robust performance, energy-efficient operation, and extensive remote monitoring capabilities. The system allows precise configuration of output power, modulation parameters, and redundancy settings to ensure optimal signal quality and reliable uptime in demanding broadcast environments.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General Page
On the General page, system information is readily available, including key details such as the device's uptime, serial number, firmware version, and location.

### Transmitter Page

The Transmitter page offers a comprehensive overview of the system’s operational status and key parameters. It enables monitoring of power levels, fault conditions, and exciter activity. Users can manage exciter selection and input sources, as well as configure automatic exciter switching to ensure reliable broadcast performance. Regular review of this page supports proactive system management and fault response.
