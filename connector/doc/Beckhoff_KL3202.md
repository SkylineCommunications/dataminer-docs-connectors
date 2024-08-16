---
uid: Connector_help_Beckhoff_KL3202
---

# Beckhoff KL3202

The **Beckhoff KL3202** is a serial connector that is used to monitor two resistance temperature detectors.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware          |
|-----------|-----------------------------|
| 1.0.0.x   | KL3202                      |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*.
- **IP port**: The port of the connected device, e.g. *4001*.
- **Bus address**: The bus address set in the device, e.g. *1* (range: *1* to *9999*).

### Configuration of Virtual Connection

The Beckhoff KL3202 element requires a virtual connection to the **Beckhoff BK9000** connector, so that this connector can provide the element with a start and stop position. These are used in the serial communication to set the relays.

To configure the virtual connection, in the **PositionInfo from BK9000** parameter, fill in the correct **PositionInfo** entry from the **Module Table** of the Beckhoff BK9000 element.

## How to use

On the **General** page, this connector displays the values of two resistance temperature detectors.
