---
uid: Connector_help_Double_D_Electronics_DDA291
---

# Double D Electronics DDA291

The DDA291 is an RF level measurement subsystem, primarily intended for measuring satellite beacon levels. It includes an internal beacon receiver which is used for signal level measurements.
The unit has four inputs (channels), for connection to LNBs; one input at a time can be selected to drive the beacon receiver. The unit includes power supplies for the LNBs, and also bias tees to inject power onto the RF inputs; all four supplies are continuously active, regardless of which input is being used.

This connector is implemented with Serial Connection through serial port.

## About

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \[SLC Main\] | Initial version  | \-           | \-                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | V1.25 dev 3            |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | \-                    | \-                      |

## Configuration

### Connections

#### IP Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: The bus/unit address of the device. The Connector uses this to create commands.

## How to use

The **General** page displays device name and software version information. Beacon Receiver current values are also displayed on this page.

**Alarms** page has displayed general alarms and Detailed Alarms Status table. Detailed Alarms Status table is created with hardcoded values for sources and types from web interface.

On **LNB** page user can find LNB Status data for all channels.

**Beacon Rx** page is configuration page where user can set values for all channels.
