---
uid: Connector_help_Agilent_N9010A-526_EXA
---

# Agilent N9010A-526 EXA

The **Agilent N9010A-526 EXA** is a spectrum analyzer device.

This connector interfaces with the spectrum analyzer and allows you to monitor the spectrum of any connected signal.

## About

### Version Info

| Range              | Features                            | Based on | System Impact |
|--------------------|-------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version (serial connector). | -        | -             |
| 1.1.0.x            | Version based on the VISA library.  | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | C.04.56            |
| 1.1.0.x | C.04.56            |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |
| 1.1.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Serial Connection — Main — 1.0.0.x only

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.

#### Virtual Connection — Main — 1.1.0.x only

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

No initialization is needed for range **1.0.0.x**.

For the **1.1.0.x range**, several things are needed:

1. Make sure the VISA library is installed on the DataMiner Agent.

   You can download the installer for the library from the [Rohde-Schwarz website](https://www.rohde-schwarz.com/us/driver-pages/remote-control/3-visa-and-tools_231388.html).

1. Make sure the DLL *RsInstrument.dll* is present in the *ProtocolScripts* folder.

1. Set the IP address of the device on the **General** page of the element.

## How to use

You can observe the spectrum on the **Spectrum Analyzer** page.
