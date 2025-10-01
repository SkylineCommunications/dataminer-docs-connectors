---
uid: Connector_help_Axon_ACP_2HS10
---

# Axon ACP 2HS10

The 2HS10 is a dual channel ultra high-quality down converter.

The **Axon ACP 2HS10** connector is used to configure and monitor the 2HS10 card.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 3130                   |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | Yes                 | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

Interface connection:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (fixed value: *2071*).
- **Bus address**: The bus address or slot number/position of the card in the frame.

#### Serial Broadcast Connection

This connector uses a smart-serial connection and requires the following input during element creation:

SMART SERIAL CONNECTION:

Interface connection:

- **IP address/host**: The polling IP or URL of the destination. Specify "any".
- **IP port**: The IP port of the destination (fixed value: *2071*).
- **Bus address**: The bus address of the device.

## How to use

The element has the following pages:

- **General**: Displays information about the identity of the card and other general information: **Card Name**, **Card Description**, **SW Revision**, **HW Revision**, etc.
- **I/O:** Contains the input and output settings and status information.
- **Down Converter A**: Contains down conversion setting parameters of Channel A.
- **Down Converter B**: Contains down conversion setting parameters of Channel B.
- **Alarm Priority:** Displays the event messages of the card, i.e. special messages generated asynchronously on the card.

> [!NOTE]
> If the setting of a parameter depends on another parameter, when the user tries to set the second parameter before the first parameter is set, a pop-up window will be displayed indicating what to do first. In this case, the user must set the first parameter according to the information in the pop-up window before setting the second parameter. For example, in order to set Coring Level (on the Down Converter pages), the Coring has to be set to *Level_dep*.

## DataMiner Connectivity Framework

The **1.0.0.x** connector range of the Axon ACP 2HS10 connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through DataMiner third-party connectors (for instance a manager).

### Interfaces

#### Fixed interfaces

Physical fixed interfaces:

- **SDI Input A**: A single fixed interface of type **in**
- **SDI Input B**: A single fixed interface of type **in**.
- **SDI HD/SD Output A**: A single fixed interface of type **out**.
- **SDI Output A**: A single fixed interface of type **out**.
- **SDI HD/SD Output B**: A single fixed interface of type **out**.
- **SDI Output B**: A single fixed interface of type **out**.

### Connections

#### Internal Connections

- **SDI Input A -> HD/SD SDI Output A**
- **SDI Input A -> SDI Output A**
- **SDI Input B -> HD/SD SDI Output B**
- **SDI Input B -> SDI Output B**
