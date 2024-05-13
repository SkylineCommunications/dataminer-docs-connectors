---
uid: Connector_help_Miranda_iControl_XML_Gateway
---

# Miranda iControl XML Gateway

The **Miranda iControl XML Gateway** retrieves all supported devices (nodes) from the XML Gateway. A limited list of device parameters is retrieved and displayed in a **DVE** (Dynamic Virtual Element) for that device.

## About

### Version Info
|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [Obsolete]     |Initial version|-         |-         |
|1.0.1.x [SLC Main]     |Make the driver Cassandra compliant|1.0.0.9         |The element needs to be recreated. Alarm and trend data will be lost.         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |iControlTM Services Gateway version 1.12         |
|1.0.1.x     |iControlTM Services Gateway version 1.12         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |Yes       |No         |-         |<ul><li><xref:Connector_help_Miranda_XVP-3901></li></ul>   |
|1.0.1.x    |Yes       |Yes         |-         |<ul><li><xref:Connector_help_Miranda_XVP-3901></li></ul>   |

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the XML Gateway
  - **IP port**: The port used by the XML Gateway.
  
## How to use

Via the **Miranda iControl XML Gateway**, a list of devices (nodes) is retrieved. Only supported devices are retrieved.

The connector currently only supports the device *Miranda XVP-3901*.

The communication to the XML Gateway is done via **serial** commands, so the parameters are retrieved one by one. Based on the number of devices, an update of a parameter could take some time.

In order to get the updates as fast as possible, the parameters are divided into **Timing Groups**, representing the priority of the parameter. The lower the group, the more frequently the parameter will be retrieved. When a Timing Group is retrieved, it will also include any parameters in a lower group. For example, when Timing Group 2 is polled, all parameters in Timing Group 1 are also retrieved.

### Device Parameters

This page provides a summary of all the supported devices. It includes their connection details, as well as status parameters like **Frame**, **Slot**, **Address**, **Global** **Status**, etc. There are also parameters indicating the **Reading Time** and indicating if the device is *Present* or *Removed.*

From this page, you can delete removed devices (DVEs) from the system.

Finally, the **Reading Info** page button displays the supported parameters and their **Timing Group**.

### Input / Output

This page provides an overview of the **Input** and **Output** configuration and the selected modes. You can amongst others find the **Input**, **BNC Output**, **Fiber Output** and **KeyFill Output** displayed here.

### Video Processing

On this page, the **Processing Mode** is indicated, and based on this, the **Gains** of a specific mode are disabled ("*N/A"*) or retrieved.

The **Advanced** page button displays additional **Gain** info for the *YCbCr* Mode, as well as additional **Offset** data.

### Audio Processing

This page displays a list of **Detected** **Groups** and **Signal** **Presence**.

For the DVE, there are two additional page buttons with the **Fixed** **Delays** of each channel.

### Audio Processing CHx-y

These pages display information on the **Audio** **Processing** for **HD** of each channel where x-y could for example be 1 and 2. It lists up until channel 16.

The pages contain the **Operation** **Mode**, **Mute**, **ABUS** selection, **Channel** selection, **Level** and the possibility to **swap** the two channels.

### Dolby Metadata Paths

On this page, you can configure the flow of the **Dolby** **Metadata** through the device, both for **Path 1** and **Path 2**

### Dolby Metadata

On this page, you can configure the metadata for the **Input** and **Output** of the two **VANC** **Streams**.
