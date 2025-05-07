---
uid: Connector_help_Pro-Bel_SW-P-08
---

# Pro-Bel SW-P-08

The Pro-Bel SW-P-08 connector provides an interface to set or remove connections in the output routing of a controlled device from remote devices. It can be used to monitor and control any router that supports the Pro-Bel SW-P-08 protocol. A serial connection is used in order to successfully retrieve and configure the matrix. A matrix is used in order to easily connect a destination with a source.

## About

### Version Info

| Range              | Key Features                                                        | Based on | System Impact                               |
|--------------------|---------------------------------------------------------------------|----------|---------------------------------------------|
| 1.0.0.x            | Initial version.                                                    | -        | -                                           |
| 1.0.1.x            | QVC Italy customer-specific branch (with hard-coded matrix labels). | -        | -                                           |
| 1.0.2.x            | DCF implementation.                                                 | -        | -                                           |
| 1.0.3.x            | Reviewed connector. Implemented latest Matrix Community Class.      | -        | -                                           |
| 1.0.4.x            | Additional functionality added.                                     | -        | -                                           |
| 1.0.5.x            | Dual Controller functionality implemented.                          | -        | Minimum required version: 10.3.11.0 - 13456 |
| 1.0.6.x [SLC Main] | Full refactoring.                                                   | -        | Minimum required version: 10.3.0.0 - 12752  |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |
| 1.0.1.x   | -                      |
| 1.0.2.x   | -                      |
| 1.0.3.x   | -                      |
| 1.0.4.x   | -                      |
| 1.0.5.x   | -                      |
| 1.0.6.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | Yes                 | Yes                     | -                     | -                       |
| 1.0.3.x   | Yes                 | Yes                     | -                     | -                       |
| 1.0.4.x   | Yes                 | Yes                     | -                     | -                       |
| 1.0.5.x   | Yes                 | Yes                     | -                     | -                       |
| 1.0.6.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: Baudrate specified in the manual of the device (default: 9600).
  - **Databits**: Databits specified in the manual of the device (default: 8).
  - **Stopbits**: Stopbits specified in the manual of the device (default: 1).
  - **Parity**: Parity specified in the manual of the device (default: No).
  - **FlowControl**: FlowControl specified in the manual of the device (default: No).

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.

## Usage

The element consists of the following pages: **General** and **Boards**.

### General

This page contains the following parameters:

- **Matrix Configuration status:** Displays any detected misconfigurations. The status **OK** indicates that the matrix was successfully configured.
- **Number of Sources:** Allows configuration of number of sources for the matrix.
- **Number of Destinations:** Allows configuration of number of destinations for the matrix.
- **Matrix Number:** Allows configuration of matrix number.
- **Level Number:** Allows configuration of level number.
- **Source Names Length:** Allows configuration of name length for sources.
- **Destination Names Length:** Allows configuration of name length for destinations.

### Boards

This page contains the **Sources** and **Destinations** tables, which contain information about the respective sources and destinations.
