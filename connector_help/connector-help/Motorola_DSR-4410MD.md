---
uid: Connector_help_Motorola_DSR-4410MD
---

# Motorola DSR-4410MD

The Motorola DSR-4410MD is a powerful digital headend product, capable of simultaneous decryption of up to 64 services. With advanced modulation
support, the DSR-4410MD can output a full transport multiplex with both MPEG-2 and/or MPEG-4 services at an information rate of up to 160 Mbps.

## About

### Version Info

| Range   | Key Features    | Based on | System Impact |
|---------|-----------------|----------|---------------|
| 1.0.0.x | Initial version | -        | -             |
| 1.1.0.x | Firmware update | 1.0.0.1  | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   |                        |
| 1.1.0.x   |                        |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION - Main Connection:

- **IP address/host**: The polling IP or URL of the destination.
- **Device address**: Not required.

SNMP Settings:

- **Port number**: The port of the connected device, by default 161.
- **Get community string**: The community string used when reading values from the device (default: public).
- **Set community string**: The community string used when setting values on the device (default: private).

## How to use

SNMP protocol is used to get the data from the device. General information about the device can be found on the
**General** page. In the event that the device needs to be restarted, the **Reset IRD** button can be used on the
**General** page.

The protocol also retrieves other relevant information from the device and displays it on the respective pages such as:
**Audio & Video**, **Input Ports & Tuning**, **Channel & Signal**, **Diagnostics**, **Retune Monitoring** and
**IP Connections**.

Each of these pages contain configuration parameters to allow the user to change specific settings of the device.