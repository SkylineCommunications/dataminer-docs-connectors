---
uid: Connector_help_Stagetec_PMT32
---

# Stagetec PMT32

The **Stagetec PMT32** is an **Analyzer**.

The Stagetec PMT32 transmits all amplified signals to the required speaker lines. It provides four separate blocks capable of routing one of two amplifier signals to eight lines. By externally connecting the individual blocks, a crosspoint matrix can be established. All connected units are monitored through measurements of all amplifier voltages, the line currents, and ground resistance.

## About

This connector retrieves data via **Serial Communication TCP/IP**. Commands are sent to the device with or without a response in return.

- This connector exports a connector that corresponds to a slot (see [Exported Connectors](#exported-connectors)).

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

| Exported Connector    | Description     |
|-----------------------|-----------------|
| Stagetec PMT32 Slot   | Slot modules    |

## Installation and configuration

### Creation

#### Serial Main connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: Not required.

## Usage

### General

The **General Page** shows if the device is still responding to the commands with the **Keep Alive Responding** and with the **Host State** parameters.
There is also the **Slot Table**, which is the main **DVE Table**, displaying the **State of each Module** and also allows the user to **rename each DVE** and hide with the **DVE Status** parameter.
