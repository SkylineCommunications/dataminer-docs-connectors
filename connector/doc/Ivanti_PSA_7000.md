---
uid: Connector_help_Ivanti_PSA_7000
---

# Ivanti PSA 7000

The Ivanti PSA 7000 is an appliance within the Ivanti Secure Access platform. It primarily serves as a gateway for secure remote access, offering various features like, application access control, and advanced threat defense.

The connector uses an **SNMP** connection.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 9.1R18.7               |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMPv2 settings:

- **Port number**: The port of the connected device, e.g. *161.*
- **Get community string**: The community string used when reading values from the device, e.g. *public*.
- **Set community string**: The community string used when setting values on the device, e.g. *private*.

## Usage

### General

This page displays general information about the device, such as the **Name**, **Location**, and **Description**.

### Interface

This page contains the **Interface**. This table information about device interfaces, such as **MTU**, **Bit Rate**, and **Bandwidth**.

The **Rate Calculation Method for Interface Table** parameter allows users to change the method of calculating the bit rate of the interface.

### Disk information

This page displays **Disk** information of the device. 

### Processes

This page displays **Monitored Processes** of the device. 

### Commands

This page displays a table which contains **Extensible Commands** of the device. 

### Load Average

This page displays a table which shows **Load Average** of the device for 1, 5 and 15 minutes.

