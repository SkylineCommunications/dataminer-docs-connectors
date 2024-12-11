---
uid: Connector_help_FOR-A_FA-9600
---

# FOR-A FA-9600

This is an SNMP-based protocol for the FOR-A FA-9600. FA-9600 multipurpose signal processors offer essential features for emerging trends in video production. They are used in many professional settings. Each of the two HD/SD inputs incorporates a frame synchronizer, and because the signal processor features 12G-SDI terminals, optional software opens the door to 4K UHD production. Adding an optional expansion card provides four more channels of 3G-SDI input or output.

## About

This connector was designed to work only with model **FA-9600**. It allows the user to monitor the state of the fans and power supplies. The status of the many inputs and outputs of this equipment sudh as Video, Audio or Slot parameters can also be monitored. SNMP **Get** commands are used to read information from the device.

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | v1.08.2            |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public1*.

## How to use

### General

This page contains general information, such as **Product Name**, **Unit Name** and **Serial number**.

Several page buttons provide access to more information about **Slot Options** or **Status** of the specific parameters of the device.

### Slot Options

This page displays information related to available slots, slot versions and firmware version of the slot.

### Status

This page provides information about the operational status of the **fans**, **power supplies**, **FPGA temperature**.

Status page contains following subpages **Video Status**, **Audio Status**, **Slot A Status**, **Slot B Status** where user can monitor statuses related to Audio, Video or Slot parameters.

### Web Interface

This page provides access to the web interface of the device. However, note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
