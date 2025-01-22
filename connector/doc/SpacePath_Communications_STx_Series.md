---
uid: Connector_help_SpacePath_Communications_STx_Series
---

# SpacePath Communications STx Series

The SpacePath Communications STx Series consists of a series of traveling-wave tube amplifiers used for different bands of satellite communication.

This device series is divided into two main product lines: the STA Series and the STR Series. The first are antenna-mount amplifiers meant for outdoor use, while the second are rack-mount amplifiers for indoor operations.

The SpacePath Communications STx Series connector uses SNMPv2 or serial communication, depending on the connector range, in order to communicate with the whole STx range of HPAs. The 2.0.0.x range using serial communication has fewer parameters available compared to the 1.0.0.x range using SNMP communication. The 2.0.0.x range should only be used in case device does not support SNMP.

## About

### Version Info

| Range              | Key Features                              | Based on | System Impact |
|--------------------|-------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version                           | -        | -             |
| 2.0.0.x            | Serial communication used instead of SNMP | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |
| 2.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 2.0.0.x   | No                  | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

#### SNMP Main Connection (1.0.0.x range)

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: The device address.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device (default value: *public*).
- **Set community string**: The community string used when setting values on the device (default value: *private*).

#### Serial Main Connection (2.0.0.x range)

This connector uses a serial connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the device e.g. 10.11.12.13.
- **IP port**: The port of the connected device.
- **Bus address**: The bus address of the connected device.

## Usage (1.0.0.x range)

### General

This page displays generic **system information**, such as the system software version, device model, connection state, and available RF bands.

### Control

This page contains several parameters that provide **control options** for the device power **amplification** (for example Attenuation, Output Route, and Linearizer state).

### Status

This page contains several parameters that **monitor** the **device state**, such as I/O Power, internal voltage values, and temperatures.

### ALC

On this page, you can define the power amplification **automatic control level settings**.

### Hardware

This page displays information related to the device hardware components.

### Meters

This page displays the internal measurements of voltages, currents, and temperatures of the HPA transistor, power supply, and other components.

### Potentiometers

This page contains **factory setting** parameters used for the **regulation** of the HPA performance.

### Faults

This page contains the **fault detection** configuration, along with flag parameters.

### Masks

This page displays the enabled/disabled **factory set fault masks**, used for fault detection.

### Server

This page contains the server communication settings, credentials, and statistical measurement parameters.

### Export

This page contains parameters used to export data.

### Redundancy

This page displays **monitoring** parameters used for **redundant systems** only.

### IP

This page is used for the **configuration** of the device **IP communication**.

### Configuration

This page contains parameters used for the **configuration of several device functionalities** (e.g. Device Control Mode, Bus Address, and Serial COM and CLI communication options).

### Web Interface

This page displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.

## Usage (2.0.0.x range)

### General

This page displays generic **system information**.

### Control

This page contains several parameters that provide **control options** for the device power **amplification**.

### Status

This page contains several parameters that **monitor** the **device state**, such as I/O Power, internal voltage values, and temperatures.

### Faults

This page contains the **fault detection** configuration, along with flag parameters.

### Web Interface

This page displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
