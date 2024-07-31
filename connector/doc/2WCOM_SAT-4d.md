---
uid: Connector_help_2WCOM_SAT-4d
---

# 2WCOM SAT-4d

The 2WCOM SAT-4d is a Professional four-channel DVB audio satellite receiver. 
The SAT-4d is the perfect DVB satellite receiver for radio networks. Based on the know-how derived from the FlexDSR series, and customer requirements, the SAT-4d offers uncompromised and reliable reception from 1 up to 4 of your audio programs from satellite.

## About

### Version Info
| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \[SLC Main\] | Initial Version  | \-           | \-                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.15.5                   |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | \-                    | \-                      |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]
- **Bus address**: [The bus address of the device.]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The **General** page displays the system information.
The **Services** page displays the list of services available in the device and their alarm status.
In **Polling Settings** page is possible to define the polling groups frequency.
