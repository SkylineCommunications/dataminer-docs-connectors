---
uid: Connector_help_Motorola_DSR-4410MD
---

# Motorola DSR-4410MD

The Motorola DSR-4410MD is a powerful digital headend product, capable of simultaneous decryption of up to 64 services. With advanced modulation
support, the DSR-4410MD can output a full transport multiplex with both MPEG-2 and/or MPEG-4 services at an information rate of up to 160 Mbps.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \            | Initial version  | \-           | \-                |
| 1.1.0.x \            | Firmware update  | \1.0.0.1     | \-                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   |                        |
| 1.1.0.x   |                        |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | \-                    | \-                      |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION - Main Connection:

- **IP address/host**: [The polling IP or URL of the destination.]
- **Device address**: [Indicate if required or not. If it is, specify default value and range.]

SNMP Settings:

- **Port number**: [The port of the connected device, by default 161.]
- **Get community string**: [The community string used when reading values from the device (default: public).]
- **Set community string**: [The community string used when setting values on the device (default: private).]
