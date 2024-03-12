---
uid: Connector_help_SEE_Telecom_eAcsys_2Rx_Us
---

# SEE Telecom eAcsys 2Rx Us

SEE Telecom eAcsys 2Rx Us is a key connector of the headend used as an HFC upstream receiver (the successor of Acsys). The integrated eAcsys platform is used for the segmentation of the CATV network.

## About

### Version Info

| Range | Features | Based on | System Impact |
|--|--|--|--|
| 1.1.0.x [SLC Main] | - Bus addresses adapted to allow addresses above 9.<br>- Conversion of Optical Power modified.<br>- Layout modified.<br>- Normalization fixed.<br>- Connector available on Repo Manager.<br>- Unnecessary parameters removed and fast timer interval reduced. | 1.0.0.x | - |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.1.0.x | 1.1                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.1.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: 10.210.64.11
- **IP port**: 161
- **Bus address**: 12

SNMP Settings:

- **Get community string**: user
- **Set community string**: private

### Initialization

No additional configuration of parameters is needed

### Redundancy

There is no redundancy defined.

## How to use

The **General** page contains basic information regarding the unit. This includes the following:

- **Identification**: Name, Type, Serial Number, Software, Hardware and BIOS Version, Rack and Slot Number
- **Statistics**: Uptime, Temperature.

The **Optical** page of this connector provides an overview of the Rx KPIs (both Rx A and Rx B), including the Status, Optical Input Power, and Wavelength. On the **Normalize Rx A** and **Normalize Rx B** subpages, you can normalize the Optical Input Power of Rx A and Rx B, respectively.

The **RF** page contains details regarding the radio frequency module for both Rx A and Rx B. You can view and modify the value for the attenuator for both Rx A and Rx B, and you can view information regarding the Automatic Level Control (ALC).

The **Switch** page displays the Unit Mode, which can be set to *Redundant* or *Segmented*. On this page, you can set the Receiver Control Switch (CTL) for both Rx A and Rx B to *Open* or *Closed*.

All of this data is retrieved using **SNMPv1**.
