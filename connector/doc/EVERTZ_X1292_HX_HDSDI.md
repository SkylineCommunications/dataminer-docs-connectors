---
uid: Connector_help_Evertz_X1202-HX_HDSDI
---

# Evertz X1202-HX HDSDI

This connector can be used to monitor and configure the Evertz X1202-HX HDSDI. This is a virtualized media processing platform that allows users to move to an infrastructure where essential core broadcast services can be applied on a generic hardware platform when required.

## About

### Version Info

| Range              | Key Features            | Based on | System Impact |
|--------------------|-------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial implementation. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector polls most of the tables using subtable functionalities to reduce the amount of time it takes to poll tables and also to poll essential rows.

In range **1.0.0.x**, the following pages are available in the element:

- **General**: Includes general system parameters like the uptime, name, and location.
- **Video**: Includes configuration and input control options for video inputs.
- **Audio**: Includes input and SS control options for audio inputs and outputs.
- **GPIO**: Includes GPI and GPO global and individual control settings.
- **Misc**: Includes various miscellaneous parameters such as Serial Address and Baud Rate.
- **Trap Management**: Allows you to manage the ability for traps to be received for management and video input sources.
- **Traps**: Includes all traps received from the device as well as detailed descriptions on what each trap does.
