---
uid: Connector_help_Leitch_Panacea_SNMP
---

# Leitch Panacea SNMP

This connector monitors the activity of the Leitch Panacea SNMP.

## About

The Panacea family of routers is available in 1RU and 2 RU frame sizes. They share a wide array of routing matrices and provide hooks for redundant power, control, and extended processing modules.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | Unknown                |

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

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

The device address needs to be configured in the element settings in order to work.

## How to use

## Main View

This page is the default page and shows the device **Matrix**.

## Status

The Status page displays information about the device in the **Physical Input Status**, **Physical Output Status**, and **PSU Overview** tables.

## Matrix Configuration

On this page, you can configure the size of the matrix by setting up the parameters **Number Of Inputs** and **Number Of Outputs**.
