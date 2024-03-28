---
uid: Connector_help_Sencore_Impulse_300D_Decoder
---

# Sencore Impulse 300D Decoder

**Impulse 300D Decoder** offers a large range output ports including SDI, HDMI®, and even analog video with RCA stereo for legacy applications. The **Sencore Impulse 300D Decoder** connector monitors and provides settings for the device through SNMP in range 1.0.x.x. and HTTP in range 1.1.x.x.

## About

### Version Info

| **Range**            | **Key Features**                                          | **Based on** | **System Impact** |
|----------------------|-----------------------------------------------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version.                                          | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | N/A                    |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main connection

In range 1.1.0.x, this connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.
- **Number of Retries**: The number of retries for HTTP commands. This should be set to "0" for write parameters to work properly.
- **Timeout of a single command (ms)**: The time between HTTP commands. This should be set to "10000" for write parameters to work properly.

#### SNMP Connection

In range 1.0.0.x, this connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **SNMP Type**: SNMPv2.
- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device (default: *ByPassProxy*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

See "1.1.0.x range" below.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### SNMP Version (1.0.0.x Range)

For the 1.0.0.x branch, the Sencore OmniHub has a limited SNMP feature set. Parameters are limited to status and configuration parameters defined in a limited MIB, and SNMP traps are not supported.

Each page contains information related to the OmniHub device such as the IP inputs and outputs, which can be configured in the associated **Settings** table.

### HTTP Version: Authentication (1.1.0.x Range)

For the range with the HTTP connection, you need to specify a username and password on the **Authentication** page of the element.
