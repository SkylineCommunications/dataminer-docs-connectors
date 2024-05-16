---
uid: Connector_help_Sencore_CRD_4900
---

# Sencore CRD 4900

Sencore CRD 4900 is a high-density modular frame designed to accommodate up to 20 cards of the openGear Multi-Definition product family.

## About

This connector contains information about the frame and overall status (Temperature, Power Supply, Buzzer, ...).


No information about the specific cards are retrievable through the Frame SNMP Agent or are provided by the MIB.
Instead, individual elements representing the cards can be created if the appropriate protocols are available.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | CRD4900-1.1.0          |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination. (default: *161*)]
- **Bus address**: [The bus address of the device. (default: *byPassProxy*)]

SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]


### Initialization

There is no additional initialization required.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

This page displays general information about the frame, such as the **Version**, **Location**, **Contact**, etc.
This page also contains the overall status, such as **Power Supply Status**, **Temperature**, **Buzzer Status**, **Front Door Status**, ... .

### Network

This page contains the network detail parameters, such as **IP Address**, **Gateway**, ... .

### Time

This page contains the time detail parameters, such as **NTP Server IP Address**, **Date Time Mode**, ... .

### Trap Config

This page contains the trap configuration events. This allows the user to specify if a trap needs to be sent out when the particular event happens.