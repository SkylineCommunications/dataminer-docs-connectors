---
uid: Connector_help_Socomec_Diris_D-50
---

# Socomec Diris D-50

The Socomec Diris D-50 is a Control and Power Supply Interface. This connector can be used to monitor and control this device.

## About

The DIRIS Digiware D-50 is a master device on the RS485 bus and master on the DIRIS Digiware bus. It can display measurements from other Socomec counters and measuring units such as Countis, Diris A, and Diris B. It centralizes data from up to 32 devices with a maximum of 186 outputs.

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
| 1.0.0.x   | No                  | Yes                     | -                     | See table below.        |

### Exported Connectors

| Exported Connector        | Description                |
|---------------------------|----------------------------|
| Socomec Diris D-50 - B-30 | Power Monitoring Device    |
| Socomec Diris D-50 - I-60 | Current Measurement Module |
| Socomec Diris D-50 - U-30 | Voltage Measurement Module |
| Socomec Diris D-50 - S-130 | Current Measurement Module |
| Socomec Diris D-50 - U-10 | Current Measurement Module |

## Installation and configuration

### Creation

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: Baudrate specified in the manual of the device.
  - **Databits**: Databits specified in the manual of the device.
  - **Stopbits**: Stopbits specified in the manual of the device.
  - **Parity**: Parity specified in the manual of the device.
  - **FlowControl**: FlowControl specified in the manual of the device.

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: The bus address of the device.

## Usage

### General

This page contains the general configuration information of the device. This includes Diris D-50 product identification parameters such as the Product ID, JBUS Table, Software Version, Vendor, etc. and various product version information.

### Connection Info

This page contains connection information such as the Ethernet IP Address, Gate, Mask, etc.

### Device Overview

This page contains a table that lists all the devices present in the current configuration along with their most important parameters.

It also displays the **Overall Polling Status** and the **Polling Steps** parameters.

The **DVE Overview** subpage contains the **B30**, **I60**, **U30**, **S130** and **U10 DVEs** tables, which display the created DVEs. It also contains the **Automatic Delete Missing Devices** button, which will automatically remove the deleted devices.
