---
uid: Connector_help_Axon_ACP_U4T240
---

# Axon ACP U4T240

The U4T240 is a 4K UHD 4-wire toolbox with optional Dolby-E processing.

The **Axon ACP U4T240** connector can be used to display and configure information related to this device.

## About

The connector can be connected to the **Axon ACP Frame Manager**.

There are different possibilities available for **alarm monitoring** and **trending**.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 1525                   |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | Yes                 | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

The element using this connector can be automatically created by the parent element using the **Axon ACP Frame Manager** connector, but it can also be a standalone element.

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **Bus address**: The bus address of the device, being the slot number of the card.

#### Serial Broadcast Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **Bus address**: The bus address of the device.

## How to use

The element has the following data pages:

- **General**: This page displays general information about the card: **Card Name**, **Card Description**, **SW Revision**, **HW Revision**, etc.
- **SFP**
- **Status**
- **Add-On**
- **I/O**
- **GPI**
- **Options**
- **Loudness**
- **Video**
- **Video Status**
- **Embedder 1**
- **Embedder 2**
- **Encoder**
- **Decoder**
- **Decoder Metadata**
- **LUT Control**
- **Network**
- **Alarm Priority**: This page displays the event messages of the card, i.e. special messages generated asynchronously on the card.

## DataMiner Connectivity Framework

The Axon ACP protocol supports the usage of DCF and can only be used on a DMA with **8.5.4** as the minimum version.

DCF can also be implemented through the DataMiner DCF user interface and through DataMiner third-party connectors (for instance a manager).

### Interfaces

#### Physical Interfaces

- **SDI Input 1**: A single fixed interface of type **input**.
- **SDI Input 2**: A single fixed interface of type **input**.
- **SDI Input 3**: A single fixed interface of type **input**.
- **SDI Input 4**: A single fixed interface of type **input**.
- **SDI Output 1**: A single fixed interface of type **output**.
- **SDI Output 2**: A single fixed interface of type **output**.
- **SDI Output 3**: A single fixed interface of type **output**.
- **SDI Output 4**: A single fixed interface of type **output**.

### Connections

#### Internal Connections

Depending on the state of the **Input Selection A**, the following connections are established:

- **SDI-1**: Between **SDI Input 1** and **SDI Output 1.**
- **SDI-2**: Between **SDI Input 2** and **SDI Output 1.**
- **SDI-3**: Between **SDI Input 3** and **SDI Output 1.**
- **SDI-4**: Between **SDI Input 4** and **SDI Output 1**.

Depending on the state of the **Input Selection B**, the following connections are established:

- **SDI-1**: Between **SDI Input 1** and **SDI Output 2.**
- **SDI-2**: Between **SDI Input 2** and **SDI Output 2.**
- **SDI-3**: Between **SDI Input 3** and **SDI Output 2.**
- **SDI-4**: Between **SDI Input 4** and **SDI Output 2**.

Depending on the state of the **Input Selection C**, the following connections are established:

- **SDI-1**: Between **SDI Input 1** and **SDI Output 3.**
- **SDI-2**: Between **SDI Input 2** and **SDI Output 3.**
- **SDI-3**: Between **SDI Input 3** and **SDI Output 3.**
- **SDI-4**: Between **SDI Input 4** and **SDI Output 3**.

Depending on the state of the **Input Selection D**, the following connections are established:

- **SDI-1**: Between **SDI Input 1** and **SDI Output 4.**
- **SDI-2**: Between **SDI Input 2** and **SDI Output 4.**
- **SDI-3**: Between **SDI Input 3** and **SDI Output 4.**
- **SDI-4**: Between **SDI Input 4** and **SDI Output 4**.
