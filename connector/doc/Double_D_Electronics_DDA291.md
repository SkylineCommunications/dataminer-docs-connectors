---
uid: Connector_help_Double_D_Electronics_DDA291
---

# Double D Electronics DDA291

The DDA291 is an RF level measurement subsystem, primarily intended for measuring satellite beacon levels. It includes an internal beacon receiver, which is used for signal level measurements.
The unit has four inputs (channels) for connection to LNBs. One input at a time can be selected to drive the beacon receiver. The unit includes power supplies for the LNBs, and also bias tees to inject power onto the RF inputs. All four supplies are continuously active, regardless of which input is being used.

This connector communicates with the device using a serial connection.

## About

| Range              | Key Features     | Based on     | System Impact     |
|--------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | V1.25 dev 3            |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### IP Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: The bus/unit address of the device. The connector uses this to create commands.

## How to use

The **General** page displays the device name and software version information, as well as the current values for the beacon receiver.

The **Alarms** page displays general alarm information as well as the Detailed Alarms Status table. This table is based on hard-coded values for sources and types from the web interface of the device.

On the **LNB** page, you can find LNB status information for all channels.

The **Beacon Rx** page is a configuration page where you can set values for all channels.
