---
uid: Connector_help_Anywave_MHPTV_CTL-M_Technical
---

# Anywave MHPTV CTL-M

## About

The Anywave MHPTV CTL-M connector enables monitoring and control of Anywave MHPTV transmitters equipped with a CTL-M controller. This connector is capable of retrieving and setting data using SNMP to communicate with the transmitter.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.

SNMP Settings:

- **IP port**: The IP port of the destination.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General Page

This page displays system identity information such as the System Name, System Description, and System Uptime, as well as network configuration (IP Address, Subnet Mask, Gateway) and firmware versions for the CTL-M controller and post amplifier modules.

### Transmitter Page

This page provides a comprehensive overview of the transmitter's operational status and key parameters such as *Forward Power*, *Reflective Power*, and *VSWR*, as well as the alarm status of these parameters.

### System Configuration Page

On this page, you can manage the transmitter as well as the exciter. Configuration options include AGC settings, transmit switch, boot controls, and exciter type, mode, band, and frequency.
