---
uid: Connector_help_CISCO_RTT_MON
---

# Cisco RTT Mon

The Cisco RTT Mon is used for measuring delay, jitter, and packet loss on the data network.

This connector uses **SNMP** polling to communicate with the device.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | No                      | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection- Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device. By default 161.
- **Get community string**: The community string used when reading values from the device (default: public).
- **Set community string**: The community string used when setting values on the device (default: private).

## Usage

### General

This page displays a table of **IP SLA Entries** and a table with the **Latest RTT Operations**. This information is read-only.

### Jitter Statistics

This page presents a table with **Jitter Statistics**.

### ICMP Jitter Statistics

This page presents a table with **ICMP** **Jitter Statistics**.
