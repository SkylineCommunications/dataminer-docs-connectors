---
uid: Connector_help_Double_D_Electronics_DDA75
---

# Double D Electronics DDA75

The DDA75 provides all the I/O required for typical remote monitoring and control applications, connecting to equipment which requires a discrete interface.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Status Query</li><li>Parallel IO Port Query</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |No firmware known         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### IP Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination.]
  - **Bus address**: [The bus address of the device.]

### Initialization

No special initialization needed, only provide IP, Port and bus address in the element settings

## How to use

On the General data page you can find the status of the first 4 ports with each 8 bit and some generic alarm flags.
