---
uid: Connector_help_CEFD_CDM-625_Serial
---

# CEFD CDM-625 Serial

The **CDM-625 Serial** Advanced Satellite Modem is intended for both closed network and legacy Intelsat applications. The CDM-625 is a replacement for the CDM-600 and CDM-600L Open Network Satellite Modems.

To further information access the link <http://www.comtechefdata.com/support/docs/satellitemodemdocs>.

About

This connector is intended to get and set information in the device via an Element in a DataMiner System, using Serial commands.

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | Initial version | - | - |
| 2.0.0.x | - | - | - |
| 3.0.0.x | - | - | - |
| 3.0.1.x | Multiple tables now uses naming instead of displayColumn to make the database for these tables Cassandra-compliant. | 3.0.0.16 | **Old trend data will be lost for these tables.** |
| 4.0.0.x | - | - | - |

## Installation and configuration

### Creation

### SERIAL CONNECTION

- **Type of Port:** the type of port used to connect to the device, default *TCP/IP*
- **IP address/host**: the polling IP of the Ethernet To Serial Converter eg *10.11.12.13*
- **IP Port**: the port addressed to connect the device, set in the Ethernet To Serial Converter, eg *4001*
- **BUS Address**: the BUS address set in the device, eg *1*

## Usage

### General

This page contains information about the system and about the overall status of the device.

### Admin-Firmware

On this page, you can set the **Base Modem** and **Packet Processor Firmware** versions.

### Admin - FAST

This page provides information about the **Equipment ID** and the installed **Hardware**.

### Config - Modem

On this page, you can set the modem's **Transmit** and **Receive** parameters. Via page buttons, you can also access the configuration for the **ACM** and **CnC** parameters.

### Config - LAN - IP

**Network Configuration**, **Per Port Configuration**, **VLAN Mode** and related parameters can be set here.

### Config - Overhead

Access this page to configure **ESC**, **AUPC** and **EDMAC**. Via the page buttons, you can set **CnC-APC** and **IDR Backward Alarms**.

### Config - Utilities

Parameters related to **Redundancy**, **Buffer**, **Unit**, **Clocks**, **Circuit ID**, **Date & Time**, **BERT Config**, **Warm-Up**, and **Save/Load Configuration** can be found here.

### Config - Drop and Insert

On this page, you can configure **Drop and Insert** and **Quad Drop and Insert** settings.

### Config - BUC / LNB

On this page you can set the **BUC** and **LNB Configuration** and also its **Status**.

### Config - PTP

The PTP feature can be configured on this page.

### Status - Modem Status

Here you can get the status of the modem's functionalities. Those can be the **Alarms**, **Rx Parameters**, **CnC**, **General Status**, **AUPC**, **WAN Statistics**, **ACM Status**, and **Fractional CnC Counters**.

### Status - Modem Logs

To get information about latest **Events** and device **Statistics**, use this page. This can be *enabled* or *disabled* through the buttons. **Initialize Pointer** is used to load from the device's memory again when polling is disabled. To mask alarms, use the **Alarm Masking** page button.

### ODU / Redundancy

On this page you can configure settings related to the **Outdoor Unit** and **Redundancy**.

### FSK

on this page you can set the FSK functionality. This functionality will generate a virtual element that contains all BUC/LNB parameters. A unique FSK Element Name can be set for the virtual element.

### Save / Load Configuration

On this page you can save all parameter values to a CSV file. You can also load such a CSV file to set the parameters to the saved values.

- By default, the file is stored in this folder: *C:\Skyline DataMiner\Documents\DMA_COMMON_DOCUMENTS\\PROTOCOLNAME\]*

- By default, the file is name *backup_ELEMENTNAME_datetime*
