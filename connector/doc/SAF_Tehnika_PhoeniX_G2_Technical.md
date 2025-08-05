---
uid: Connector_help_SAF_Tehnika_Phoenix_G2_Technical
---

# SAF Tehnika Phoenix G2

## About

The SAF Tehnika Phoenix G2 is a high-capacity point-to-point microwave radio system designed for robust and flexible data transmission. It supports channel bandwidths up to 80 MHz and offers capacities up to 1 Gbps in 2+0 configurations. The system integrates advanced modulation schemes, including 1024QAM, and provides seamless transition from TDM-only or ASI-only networks to hybrid native ASI/T1/E1/IP networks.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.

- **IP port**: The IP port of the destination.

- **Bus address**: The bus address of the device.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).

- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to use

The element consists of the data pages detailed below:

- **General**: Contains the main KPIs related to radios on the device.

- **Radio Configuration**: Contains all configuration values for both radios, including both receiving and transmitting values.

- **Temperature**: Displays temperature readings from the device.
