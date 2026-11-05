---
uid: Connector_help_DekTec_DTE-3100
---

# DekTec DTE-3100

DekTec DTE-3100 is a **Transport Stream over IP to ASI Gateway (Receiver)**. The unit accepts unicast and multicast streams over its Gigabit-Ethernet port and de-encapsulates the TSoIP streams to an ASI output. Key features include de-encapsulation of UDP or RTP, accurate timing reconstruction using innovative algorithms to overcome IP jitter, as well as error correction according to SMPTE 2022-1. The connector can be used to view real-time parameters from the device and to configure parameters of the device.

## About

The connector is intended to work with the **DTE-3100**. SNMP communication is used to monitor the different parameters of the device.

### Version Info

| Range   | Key Features           | Based on | System Impact |
|---------|------------------------|----------|---------------|
| 1.0.0.x | Initial version. SNMP. | -        | -             |

### Product Info

| Range   | Supported Firmware Version |
|---------|----------------------------|
| 1.0.0.x | 16                         |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

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

## Usage

### General

This page displays general information (Name, Serial Number, Firmware version, etc.), as well as information about **Watchdog** and about **Power Cycle counters** on the **Counters** subpage.

### Status

The page shows the different values for two sets of settings: **Transcoding** (Packet Size, Transport Stream Rate, Operational Status, Addressing Method, IP Port, and IP Jitter Tolerance) and **SMPTE Protocol** (Protocol, Transport Packets per IP, FEC Rows and Columns, IP Lost Before, and After FEC).

### Network

On this page, you can configure the following parameters: **Multicast Address**, **IP Source Multicast**, **Generate Trap**, **Trap Community**, **Trap Port**, and **Trap Destination**.

### SMPTE Settings

This page contains parameters such as **FEC Reconstruction**, **Output Delay**, **Transport Stream Rate**, **Transport Stream Packet Size**, **Transport Stream Estimation Mode**, **IP Jitter Error Counter**, **FEC Delay**, **Delay Factor**, etc.

### Web Page

On this page, you can access the web interface of the device.

Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
