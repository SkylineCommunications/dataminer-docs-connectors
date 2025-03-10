---
uid: Connector_help_DekTec_DTE-3120
---

# DekTec DTE-3120

**DekTec DTE-3120** is a networked DVB-ASI input adapter (transmitter). This connector can be used to view real-time parameters from the device and to configure parameters of the device.

## About

This connector is intended to work with the **DTE-3120**. SNMP communication is used to monitor the different parameters of the device.

### Version Info

| Range   | Description            | DCF Integration | Cassandra Compliant |
|---------|------------------------|-----------------|---------------------|
| 1.0.0.x | Initial version. SNMP. | No              | Yes                 |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | 15                          |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## Usage

### General

This page displays general information (Name, Serial Number, Firmware version, etc.). Via the **More** page button, you can also view information about Bytes Received and ASI Code Violations.

### Status

The page shows the different values for two sets of settings: **Transcoding** (IP Address Status, Input Status, Channel Status, Transport Stream Rate, IP Port, Time to Life, and Type of Service) and **SMPTE Protocol** (Protocol, Transport Packets per IP, FEC Rows and Columns, IP Lost Before and After FEC, and Transport Stream Packet Size).

### Network

On this page, you can configure the following parameters: **IP Address**, **IP Source Multicast**, **Channel**, **Physical Port**, **Generate Trap**, **Trap Community**, **Trap Port**, and **Trap Destination**.
