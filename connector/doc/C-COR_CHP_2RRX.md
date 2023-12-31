---
uid: Connector_help_C-COR_CHP_2RRX
---

# C-COR CHP 2RRX

This connector is automatically generated by the connector **C-COR CHP SMM**, version 2.0.0.x. It is an SNMP-based connector that is used to monitor and configure the **C-COR CHP 2RRX**.

## About

This connector provides a monitoring interface for the **C-COR CHP 2RRX** chassis.

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 2.0.0.x          | Boot v001.000               |

## Installation and configuration

### Creation

This connector is used by DVE child elements that are **automatically created** by the parent connector [C-COR CHP SMM](xref:Connector_help_C-COR_CHP_SMM).

## Usage

### General

This page contains general information about the card, such as the **Physical State**, **Reset Cause**, **Mode of Operation**, **Local Control**, **Module State** and **Internal Temperature**.

There are also two page buttons:

- **Device Info**: Displays the parameters **Module**, **Module Name**, **Serial Number**, **Hardware**, **Firmware**, **Bootdown**, etc.
- **Internal Threshold:** Allows you to configure both **Major (High and Low)** and **Minor (High and Low)** thresholds for **Input Power** **A** and **B** and for **Internal Temperature**.

### Optical

This page displays the **Optical Power**, **Control**, **Wavelength** and **Optical Status** for **A** and **B** receivers.

The **Normalize** page button opens a subpage where the **Optical Power A** and **B** can be normalized.

### RF

This page displays the **Output State**, **Channel Control**, **Low Attenuation** and **Total Attenuation** for **A** and **B** receivers.
