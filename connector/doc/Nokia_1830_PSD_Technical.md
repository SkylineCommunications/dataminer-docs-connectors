---
uid: Connector_help_Nokia_1830_PSD_Technical
---

# Nokia 1830 PSD

## About

The **Nokia 1830 Photonic Service Demarcation (PSD)** is Network Interface Device (NID) used for network demarcation at customer premises. It supports MEF-compliant 10G Ethernet and wavelength services by extending the optical network.

This connector uses the SNMP protocol to communicate with the **Nokia 1830 PSD** device.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection. This is the main connection used to retrieve all the data. It requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to use

The connector is designed to monitor the device's network interfaces, raise alarms when necessary, and enable a timely response to network events.

The General page provides basic information about the device (e.g. name, model, and IP address).

The other three pages present detailed interface metrics, including input/output bit rate, packet rate, operational status, and other relevant parameters.
