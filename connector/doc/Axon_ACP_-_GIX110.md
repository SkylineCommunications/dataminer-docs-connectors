---
uid: Connector_help_Axon_ACP_-_GIX110
---

# Axon ACP - GIX110

The GIX110 is a dual-channel 3 Gb/s, HD, SD integrity checking probe with optional clean audio (2x1) switchover function.

The **Axon ACP - GIX110** connector can be used to display and configure information related to this device.

## About

This connector is automatically generated by the connector **Axon ACP**.

There are different possibilities available for **alarm monitoring** and **trending**.

### Version Info

| Range     | Description                        | DCF Integration     | Cassandra Compliant     |
|------------------|------------------------------------|---------------------|-------------------------|
| 1.0.2.x          | Change in export rules.            | Yes                 | Yes                     |
| 1.0.3.x          | Change in discrete display values. | Yes                 | Yes                     |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.2.x          | 1010, 1113, 1515, 1616      |
| 1.0.3.x          | 1010, 1113, 1515, 1616      |

## Installation and configuration

### Creation

This element is automatically created by the parent element using the **Axon ACP** connector.

## Usage

This element has the following data pages:

- **General**: This page displays general information about the card: **Card Name**, **Card Description**, **SW Revision**, **HW Revision**, etc.
- **Status**
- **Video**
- **Video Probe**
- **Audio A**
- **Audio B**
- **Audio Probe**
- **GPI**
- **Settings**
- **Embedder**
- **Embedder A/B**
- **Embedder C/D**
- **Network**
- **Alarm Priority**: This page displays the event messages of the card, i.e. special messages generated asynchronously on the card.

## DataMiner Connectivity Framework

The Axon ACP connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through DataMiner third-party connectors (for instance a manager).

Connectivity for this protocol is managed by the parent protocol Axon ACP.

### Interfaces

#### Physical Interfaces

- **SDI Input A**: A single fixed interface of type **input**.
- **SDI Input B**: A single fixed interface of type **input**.
- **SDI Input C**: A single fixed interface of type **input**.
- **SDI Input D**: A single fixed interface of type **input**.
- **REF Input 1**: A single fixed interface of type **input**.
- **REF Input 2**: A single fixed interface of type **input**.
- **QUAD-SPEED SYNAPSE Bus Input**: A single fixed interface of type **input**.
- **SDI Output A1**: A single fixed interface of type **output**.
- **SDI Output A2**: A single fixed interface of type **output**.
- **SDI Output B1**: A single fixed interface of type **output**.
- **SDI Output B2**: A single fixed interface of type **output**.
- **QUAD-SPEED SYNAPSE Bus Output**: A single fixed interface of type **output**.
