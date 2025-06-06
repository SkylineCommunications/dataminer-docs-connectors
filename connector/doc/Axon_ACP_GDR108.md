---
uid: Connector_help_Axon_ACP_GDR108
---

# Axon ACP GDR108

The GDR108 is a 3 Gb/s, HD and SD dual-input distribution amplifier with 8 reclocked outputs (ASI/DVB compatible).

The **Axon ACP GDR108** connector can be used to display and configure information related to this device.

## About

This connector can be automatically generated by the connector **Axon ACP**.

There are different possibilities available for **alarm monitoring** and **trending**.

### Version Info

| Range     | Key Features                 | Based on     | System Impact     |
|-----------|------------------------------|--------------|-------------------|
| 1.0.0.x   | Initial version [SLC Main]   | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 0500, 0600, 0800       |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | Yes                 | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

The element using this connector can be automatically created by the parent element using the **Axon ACP** connector, but it can also be a standalone element.

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

## Usage

This element has the following data pages:

- **General**: This page displays general information about the card: **Card Name**, **Card Description**, **SW Revision**, **HW Revision**, etc.
- **SFP**
- **Status**
- **Settings**
- **HDMI/CVBS**
- **Alarm Priority**: This page displays the event messages of the card, i.e. special messages generated asynchronously on the card.

## DataMiner Connectivity Framework

The Axon ACP connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through DataMiner third-party connectors (for instance a manager).

### Interfaces

#### Physical Interfaces

- **SDI Input**: A single fixed interface of type **input**.
- **SDI Output 1**: A single fixed interface of type **output**.
- **SDI Output 2**: A single fixed interface of type **output**.
- **SDI Output 3**: A single fixed interface of type **output**.
- **SDI Output 4**: A single fixed interface of type **output**.
- **SDI Output 5**: A single fixed interface of type **output**.
- **SDI Output 6**: A single fixed interface of type **output**.
- **SDI Output 7**: A single fixed interface of type **output**.
- **SDI Output 8**: A single fixed interface of type **output**.

#### Virtual Interfaces

- **Reclocker**: A single fixed interface of type **inout**.

### Connections

#### Internal Connections

When a DVE child element is created, the following connections are established:

- Between **SDI Input** and **Reclocker**.
- Between **Reclocker** and **SDI Output 1**.
- Between **Reclocker** and **SDI Output 2**.
- Between **Reclocker** and **SDI Output 3**.
- Between **Reclocker** and **SDI Output 4**.
- Between **Reclocker** and **SDI Output 5**.
- Between **Reclocker** and **SDI Output 6**.
- Between **Reclocker** and **SDI Output 7**.
- Between **Reclocker** and **SDI Output 8**.
