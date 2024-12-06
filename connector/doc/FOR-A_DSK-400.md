---
uid: Connector_help_FOR-A_DSK-400
---

# FOR-A DSK-400

The DSK-400 is a digital downstream keyer which accepts 4 background (Line) video and 4 title 
inputs (Fill and Key) in both 1080p (Level-A) and 1080i. 
It can superimpose title text over incoming video to output combined signals. A chromakey function 
is also available as an option.

This connector uses a serial connection oveer UDP/IP port to communicate with the device.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | v1.08.2           |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Serial connection - Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device. (Default UDP/IP port is 8740)
  - **Bus address**: The bus address of the device.

## How to use

The **General** page displays Superimpose statuses for all of 4 Superimpose values. The user can easily configure and read the Superimpose Status, Transition Rate, Clip and Gain values for each Superimpose.
