---
uid: Connector_help_Axon_ACP_ERS10_-_HEB05
---

# Axon ACP ERS10 - HEB05

The HEB05 is an **HD SDI** and **SD SDI** digital audio embedder. It is capable of inserting or appending 4 free-running **AES/EBU** digital audio channels (8 channels). The core of the HEB05 consists of 4 embedder blocks (A -\> D). Each block is capable of embedding 4 audio channels into one group, for a total of 16 audio channels in 4 groups. In addition, 4 **ADD-ON** cards can be connected to create a routing matrix. One ADD-ON card is needed to get 16 embedded channels (DIO48).

The **Axon ACP ERS10 - HEB05** connector can be used to display and configure information of the related device.

## About

A **serial** connection is used in order to successfully retrieve and configure the device's information. There are also different possibilities available for **alarm monitoring** and **trending**.

This connector is automatically generated by the connector **Axon ACP ERS10.**

### Product Info

The table below indicates which device revision is available since a specific connector version. Every connector version, within the same range, also supports the previously implemented revisions.

| **Connector Version** | **Device Revision** |
|--------------------|---------------------|
| 1.0.0.1            | Rev. 07             |
| 1.0.1.1            | Rev. 07             |
| 1.2.0.1            | Rev. 07             |
| 2.1.0.1            | Rev. 07             |
| 2.2.0.1            | Rev. 07             |

## Installation and configuration

### Creation

This connector is used by DVEs that are automatically created by the parent element. No user input is required.

## Usage

### General

This page contains generic information: **Card Name**, **Slot Number**, **Card ID**, **Software Revision**, **Hardware Revision**, etc.

### Status

### Add On

This page contains the **Add On** configuration settings.

### Settings

This page contains the card's generic settings: **Preset**, **SDI Format**, **Field Frequency**, **Emb Mode**, etc.

### AES

This page contains the AES-related configuration settings: **Delay**, **Gain** and **Phase**.

### Embedder

This page contains the configuration settings for each of the embedders: **Selection**, **1/2** and **3/4**.

### Alarm Priority

This page contains the individual priority settings for the supported events.
