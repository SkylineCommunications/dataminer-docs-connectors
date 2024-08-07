---
uid: Connector_help_LYNX_Technik_AG_Series_5000
---

# LYNX Technik AG Series 5000

This connector monitors the activity of the Lynx Technik AG Series 5000 device. Series 5000 is a rack-based terminal equipment solution that can be user-configured with any combination of card modules from an extensive range of available solutions. This includes audio distribution, conversion and processing, as well as video distribution, conversion, embedding and de-embedding, frame synchronization, test generators, downconverters and video processors.

## About

This connector polls data from the device using a **smart-serial** connection. For each of the card modules, a DVE is generated.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range   | Supported Firmware Version | Serial Protocol Version |
|---------|----------------------------|-------------------------|
| 1.0.0.x | 8.8.1                      | 1.9                     |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components    |
|-----------|---------------------|-------------------------|-----------------------|------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | See table below.       |

### Exported Connectors

| Exported Connector                       | Description                                               |
|------------------------------------------|-----------------------------------------------------------|
| LYNX Technik AG Series 5000 - RCT 5023-G | Rack Controller                                           |
| LYNX Technik AG Series 5000 - DVD 5820   | Switching and Distribution Unit                           |
| LYNX Technik AG Series 5000 - PDM 5380   | Audio Embedder                                            |
| LYNX Technik AG Series 5000 - PVD 5802   | Frame Synchronizer                                        |
| LYNX Technik AG Series 5000 - DVA 5718-L | Analog Video Distribution Amplifier with RollCall Control |
| LYNX Technik AG Series 5000 - CDX 5624   | Downconverter                                             |
| LYNX Technik AG Series 5000 - PVD 5810   | Frame Synchronizer                                        |
| LYNX Technik AG Series 5000 - PVD 5840-D | Frame Synchronizer                                        |
| LYNX Technik AG Series 5000 - PMX 5364   | Audio Embedder                                            |
| LYNX Technik AG Series 5000 - DAA 5321   | Analog Audio Distribution Amplifier                       |
| LYNX Technik AG Series 5000 - DAD 5220   | Dual AES Audio Distribution Amplifier                     |
| LYNX Technik AG Series 5000 - DVD 5810   | SDI/ASI Distribution Amplifier                            |
| LYNX Technik AG Series 5000 - DVO 5820   | Dual SDI/ASI Distribution Amplifier with Fiber I/O        |
| LYNX Technik AG Series 5000 - ORR 1802   | Dual 3G Fiber-Optic-to-SDI Receiver                       |
| LYNX Technik AG Series 5000 - ORX 1702   | Analog Sync / Video Fiber-Optic Receiver                  |
| LYNX Technik AG Series 5000 - ORX 5800   | Quad Fiber-Optic-to-SDI Receiver                          |
| LYNX Technik AG Series 5000 - OTT 1812   | Dual 3G SDI-to-Fiber-Optic Transmitter                    |
| LYNX Technik AG Series 5000 - OTX 1712   | Analog Sync / Video Fiber-Optic Receiver                  |
| LYNX Technik AG Series 5000 - RCT 1012   | Rack Controller                                           |
| LYNX Technik AG Series 5000 - SPG 1707   | HD / SD Sync Pulse Generator with Genlock                 |
| LYNX Technik AG Series 5000 - OTX 5840   | Quad SDI-to-Fiber-Optic Transmitter                       |
| LYNX Technik AG Series 5000 - CHD 1402-G | 4K HDMI-to-12G-SDI Converter                              |

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
  - **IP port**: The IP port of the device. The default IP port is *2306.*

### Configuration

To make sure the connector works correctly, on the **General** page, set the **Child Completion State** parameter to *Enabled.*

## Usage

### General

This page displays information about the **Stacks**, **Controllers** and **Cards** available in the device.

It is also possible to view the **Serial Protocol Version** of the device here and to enable or disable the **Child Completion State**.

The parameter **Time Since Last Pushed Data** displays the time in seconds since the device and the element communicated with each other.

### Overview

On this page, a **tree view** displays the current modules of the device grouped by **Stacks**, **Controllers** and **Cards**.

### DVE

Each module table on this page displays the DVEs created by the main element. If a card is not available in the device, you can delete the corresponding DVE child element by pressing the **Remove** button.

You can also enable an **Automatic Removal** option or **Remove All** DVEs of the cards that are not available in the device.

## Note

On the General page, the **Child Completion State** must be *Enabled* in order for the connector to work.
