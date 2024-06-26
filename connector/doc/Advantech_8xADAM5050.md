---
uid: Connector_help_Advantech_8xADAM5050
---

# Advantech 8xADAM5050

The 8xADAM-5050 features sixteen digital input channels for the 8 modules available on the device, summing up to a great total of 128 inputs in the Status table. The switches can be used to control solid-state relays, which in turn can control heaters, pumps, and power equipment. The ADAM-5000 can use the module's digital inputs to determine the state of limit or safety switches, or to receive remote digital signals.

The connector uses **serial** communication with the device. It is possible to invert the mode line.

## About

### Version Info

| Range     | Key Features                                          | Based on     | System Impact     |
|-----------|-------------------------------------------------------|--------------|-------------------|
| 1.0.0.x   | Initial version                                       | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 1.29                   |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components    | Exported Components    |
|-----------|---------------------|-------------------------|----------------------|------------------------|
| 1.0.0.x   | No                  | Yes                     | -                    | -                      |


## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device, by default *502*.

## Usage

This connector consists of a table **Status** on the **General** page.

On that page, you can find all 16 channels for the 8 modules. The table has 128 entries where is possible to see the current status of the input and set it.

This connector also has InterApp available to do remote sets from a different connector.
