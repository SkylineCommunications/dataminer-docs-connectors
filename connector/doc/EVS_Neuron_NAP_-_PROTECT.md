---
uid: Connector_help_EVS_Neuron_NAP_-_PROTECT
---

# EVS Neuron NAP - PROTECT

This connector is intended to be used with the Neuron PROTECT, which provides the protect function of the EVS Neuron.

## About

### Version Info

| Range              | Features         |Based on  |System Impact |
|--------------------|------------------|----------|--------------|
| 1.0.0.x [SLC Main] | Initial version. |-         |-             |

### Product Info

**This subsection can only be omitted for a virtual connector**

In this subsection, insert a table with two columns. In the table, list the firmware versions that are fully compatible with the connector, together with the connector ranges. If multiple firmware versions are compatible with one connector range, add them in the same row, but on different lines.

|Range    |Supported Firmware  |
|---------|--------------------|
|1.0.0.x  |5.9.4               |

### System Info

|Range    |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|-----------------|---------------------|-------------------|----------------------|
|1.0.0.x  |No               |Yes                  |-                  |-                     |

## Configuration

### Connections

#### IP Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:



- Interface connection:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *2072*)]

## How to use

IThe connector does not have a polling timer. It only polls the data at element startup. However, there is also a button available that allows you to trigger the polling manually.

After element startup, the connector can also receive events (unsolicited messages).

### General

This page contains card information parameters, such as the **Card Name**, **Product Version**, and **Card Description**.

### General Settings

This page includes the **Gen Lock Settings**, **Input Stream Configuration**, and **De-Embedders** parameters as well as buttons for pop-up pages.

### Network Settings

This page contains network-related tables such as **MAC settings, MAC DNS Settings**, and **MAC Statistics.**

### IP Video I/O

This page contains tables for **Video Input/Output Streams** as well as **Video Output Backup Streams.**

### IP Audio I/O

This page contains tables for **Audio Input/Output Streams** as well as **Audio Output Backup Streams.**

### SDI I/O

This page contains tables for **SDI Static I/O** and **SDI Bidirectional I/O.**

### Audio Paths

This page contains tables for **De-Embedded Audio** and **IP Audio.**

### Video Paths

This page contains tables for **Video Formats, Video Paths**, and **Video Paths Color Correction.**

### Chassis

This page contains chassis information parameters, such as **Board**,** IO Board,** **Board Temperature**, and **SMARC**.

### Power Supply Unit

This page displays **Fan Control, Power Consumption**, and **Temperature** parameters, as well as the **Power Supply Units** table.

### Management Port

This page contains parameters related to **Ethernet** and **DNS**.

### Network interface Modules

This page contains **SQFP** and **SFP** tables.

