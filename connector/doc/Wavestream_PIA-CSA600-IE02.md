---
uid: Connector_help_Wavestream_PIA-CSA600-IE02
---

# Wavestream PIA-CSA600-IE02

This is a serial protocol for the **Wavestream SSPA**.

The connector is used to **monitor** and **configure** the device.

## About

A serial connection is needed for the connector so it can retrieve and send information from/to the device.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | V2.93                  |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | Yes                 | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

#### Serial main connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device, by default *4001*.
  - **Bus address**: The bus address of the device, by default *0*.

## Usage

### General

This page displays general information such as the **Model Number**, **Serial Number**, and **Version**.

It also includes more specific parameters such as the **Temperature**, **Current**, **Voltage**, etc.
