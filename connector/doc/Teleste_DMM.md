---
uid: Connector_help_Teleste_DMM
---

# Teleste DMM

This connector monitors and manages controller devices like the Teleste DMM and all of its modules. It polls and sets parameters both of the controller device itself and of the attached modules.

## About

Several parameters of the controller itself are polled with a timer. With a separate timer, all of the modules are polled one after another. When a set occurs on one of the attached modules, this polling cycle is interrupted (as soon as the current polling of the current module is finished) in order to give priority to the set.

Every module has its own interface (i.e. IP address and port). This is the reason why 2 serial connections are used in the connector, one for the controller device and one for the modules. The modules connection changes for every module that needs to be polled/set.

This connector exports different connectors based on the retrieved data. A list can be found in the section "Exported connectors" below.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | See table below.        |

### Exported Connectors

| Exported Connector   | Description                                                                            |
|----------------------|----------------------------------------------------------------------------------------|
| Teleste DMM DBM100   | DBM100                                                                                 |
| Teleste DMM DVO101   | DVO101                                                                                 |
| Teleste DMM DVO202   | DVO202 (from v1.0.0.2)                                                                 |
| Teleste DMM DVO202 S | DVO202 S (from v1.0.0.11)<br>DVO202 NL (from v1.0.0.12)                                |
| Teleste DMM DVO421   | DVO421 (from v1.0.0.7)                                                                 |
| Teleste DMM DVO624   | DVO624 (from v1.0.0.2)                                                                 |
| Teleste DMM DVO802   | DVO802 (from v1.0.0.2)                                                                 |
| Teleste DMM DVO902   | DVO902/2E (from v1.0.0.11)<br>DVO902/5E (from v1.0.0.11)<br>DVO902/8E (from v1.0.0.15) |
| Teleste DMM DVO902_8 | DVO902/5 (from v1.0.0.15)<br>DVO902/8 (from v1.0.0.5)                                  |
| Teleste DMM DVP332   | DVP332                                                                                 |
| Teleste DMM DVP432   | DVP432 (from v1.0.0.2)                                                                 |
| Teleste DMM DVP532   | DVP532                                                                                 |
| Teleste DMM HDO903   | HDO903 (from v1.0.0.11)                                                                |
| Teleste DMM HDO905   | HDO905 (from v1.0.0.11)                                                                |
| Teleste DMM HDO906   | HDO906 (from v1.0.0.11)                                                                |
| Teleste DMM HDP230   | HDP230 (from v1.0.0.13)                                                                |
| Teleste DMM HDO202   | HDO202 (from v1.0.0.16)                                                                |

## Installation and configuration

### Creation

#### Serial Main connection

This connector uses a serial connection to request data from the **controller**. This connection requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.

#### Serial Modules connection

This additional serial connection is used to request data from the **modules**.

No user configuration is required. The connector will dynamically set the IP address and IP port depending on which module is polled.

## Usage

### Properties

This page displays general information about the hardware and software.

### DVX Devices

This page displays an overview of the modules attached onto the DVX bus.

For each of the attached modules, an entry is made in the DVX device table on this page and a new DVE child element is created.

### Addresses

This page displays network information for the controller device.

### Statistics

This page displays supply voltage and controller information for the controller device.

### Modem

This page displays modem functions.

### Settings

This page displays controller-specific settings.
