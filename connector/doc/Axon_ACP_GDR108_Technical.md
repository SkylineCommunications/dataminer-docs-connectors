---
uid: Connector_help_Axon_ACP_GDR108_Technical
---

# Axon ACP GDR108

## About

The GDR108 is a 3 Gb/s, HD and SD dual-input distribution amplifier with 8 reclocked outputs (ASI/DVB compatible).

The **Axon ACP GDR108** connector can be used to display and configure information related to this device.

There are different possibilities available for **alarm monitoring** and **trending**.

## Configuration

### Connections

#### Serial Connection – Unicast Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device.

#### Serial Connection – Broadcast Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device. Should be set to "any".

## How to use

All the information that can be useful for monitoring can be found in a tree view on the **Generic** data page and on the pages **Status** and **Settings**.

## DataMiner Connectivity Framework

The 1.0.0.x range of the Axon ACP GDR108 connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (e.g. a manager).

### Interfaces

#### Fixed Interfaces

Virtual Fixed interfaces:

- **Reclocker**: A single fixed interface of type **inout**

Physical Fixed interfaces:

- **SDI Input**: A single fixed interface of type **input**.
- **SDI Output 1**: A single fixed interface of type **output**.
- **SDI Output 2**: A single fixed interface of type **output**.
- **SDI Output 3**: A single fixed interface of type **output**.
- **SDI Output 4**: A single fixed interface of type **output**.
- **SDI Output 5**: A single fixed interface of type **output**.
- **SDI Output 6**: A single fixed interface of type **output**.
- **SDI Output 7**: A single fixed interface of type **output**.
- **SDI Output 8**: A single fixed interface of type **output**.

### DCF Connections

#### Internal Connections

- Between **SDI Input** and **Reclocker**.
- Between **Reclocker** and **SDI Output 1**.
- Between **Reclocker** and **SDI Output 2**.
- Between **Reclocker** and **SDI Output 3**.
- Between **Reclocker** and **SDI Output 4**.
- Between **Reclocker** and **SDI Output 5**.
- Between **Reclocker** and **SDI Output 6**.
- Between **Reclocker** and **SDI Output 7**.
- Between **Reclocker** and **SDI Output 8**.
