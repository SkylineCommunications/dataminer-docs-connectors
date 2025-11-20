---
uid: Connector_technical_Pro-Bel_SW-P-08_2.0.0.X
---

# Pro-Bel SW-P-08 (2.0.0.X)

## About

Pro-Bel SW-P-08 is used to communicate with routers that implement general remote control protocol SW-P-08. It allows management and monitoring of the crosspoints.

## Configuration

### Connections

#### Smart-Serial connection

This connector uses a smart-serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Accepted IP address**: The IP of the device from which to accept messages.

The following are defined by the protocol documentation and are set as defaults:
  - **Baudrate**: Baudrate specified in the documentation (default: 9600).
  - **Databits**: Databits specified in the documentation (default: 8).
  - **Stopbits**: Stopbits specified in the documentation (default: 1).
  - **Parity**: Parity specified in the documentation (default: No).
  - **FlowControl**: FlowControl specified in the documentation (default: No).

## How to Use

The element has the following data pages: **General** and **Router Control**.

### General

This page contains the following parameters:

- **Matrix Configuration status:** Displays any detected misconfigurations. The status **OK** indicates that the matrix has been successfully configured.
- **Number of Sources:** Allows you to configure the number of sources for the matrix.
- **Number of Destinations:** Allows you to configure the number of destinations for the matrix.
- **Matrix Number:** Allows you to configure the matrix number.
- **Level Number:** Allows you to configure the level number.
- **Source Names Length:** Allows you to configure the name length for sources.
- **Destination Names Length:** Allows you to configure the name length for destinations.

### Router Control

This page contains the **Sources** and **Destinations** tables, which contain information about the respective sources and destinations.

## Notes

Minimum required DataMiner version for the connector is **10.3.0.0 - 12752**.