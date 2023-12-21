---
uid: Connector_help_Sony_Signal_Processing_Unit-NXLK-IP45F
---

# Sony Signal Processing Unit-NXLK-IP45F

The **Sony NXL-FR316** and **Sony NXL-FR318** are processing units (chassis), to which different cards can be attached:

- IP converter boards: Sony NXL-IP40F/41F/42F/45F/50Y

## About

This connector is designed to monitor the state of the IP Converter board that can be connected to a **Sony NXL-FR316** and **Sony NXL-FR318**, using **SNMP** communication.

This connector is exported by the parent connector **Sony Signal Processing Unit**, from version 1.0.0.x onwards.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | V1.00                  |

## Configuration

### Initialization

This connector is used by DVEs that are **automatically created** by the parent element. No user input is required.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### Status

This page displays detailed status information on the module, including the **Device ID**, **Manufacturer**, **Model**, **Destination**, **Serial Number**, **Category, Version**, **Model Suffix** and **Version Suffix**.

### Alarms

This page displays the **Error Statuses** connected to this module.

### NMI

This page allows you to connect this IP Board to the selected **NMI**. Note: only 1 NMI element can be connected to 1 IP Board Connected to this chassis. You can check which NMI element is connected to which IP Board via the **NMI** table on the main element.
