---
uid: Connector_help_Pro-Bel_SW-P-08
---

# Pro-Bel SW-P-08

The Pro-Bel SW-P-08 connector provides an interface to set or remove connections in the output routing of a controlled device from remote devices. It can be used to monitor and control any router that supports the Pro-Bel SW-P-08 protocol. A serial connection is used in order to successfully retrieve and configure the matrix. A matrix is used in order to easily connect a destination with a source.

## About

### Version Info

| Range   | Key Features                                                        | Based on | System Impact                               |
|---------|---------------------------------------------------------------------|----------|---------------------------------------------|
| 1.0.0.x | Initial version.                                                    | -        | -                                           |
| 1.0.1.x | QVC Italy customer-specific branch (with hard-coded matrix labels). | -        | -                                           |
| 1.0.2.x | DCF implementation.                                                 | -        | -                                           |
| 1.0.3.x | Reviewed connector. Implemented latest Matrix Community Class.      | -        | -                                           |
| 1.0.4.x | Additional functionality added.                                     | -        | -                                           |
| 1.0.5.x | Dual Controller functionality implemented.                          | -        | Minimum required version: 10.3.11.0 - 13456 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |
| 1.0.1.x   | -                      |
| 1.0.2.x   | -                      |
| 1.0.3.x   | -                      |
| 1.0.4.x   | -                      |
| 1.0.5.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.0.1.x   | No                  | Yes                     | -                     | -                       |
| 1.0.2.x   | Yes                 | Yes                     | -                     | -                       |
| 1.0.3.x   | Yes                 | Yes                     | -                     | -                       |
| 1.0.4.x   | Yes                 | Yes                     | -                     | -                       |
| 1.0.5.x   | Yes                 | Yes                     | -                     | -                       |

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
  - **Bus address**: The "Matrix Number", "Level Number", "Number of Inputs", and "Number of Outputs" of the matrix, separated by a period ("."). The range of inputs and outputs is 1-1024. For instance: "*1024.1024*".

## Usage

The element consists of the following pages: **Matrix**, **General**, **Inputs/Outputs** and **Labels**.

### Matrix

This page contains the matrix, sized according to the **Number of Inputs** and **Number of Outputs** specified during configuration.

### General

This page contains the following parameters:

- **Matrix Configuration:** Displays any detected misconfigurations. The status **OK** indicates that the matrix was successfully configured.
- **Number of Inputs:** Displays the selected number of inputs for the matrix.
- **Number of Outputs:** Displays the selected number of outputs for the matrix.
- **Enable Interrogate Commands As Backup**: Enables sending a backup command in cases where the tally command does not retrieve all crosspoints.
- **Last KeepAlive Timestamp:** Displays the last timestamp received.
- **Number of Wrong CRCs Received**: The number of wrong CRCs received on a message.
- **Name Length**: The number of characters of a name.
- **Refresh Names:** This button allows you to refresh the associated destination and source names.

Starting from range 1.0.5.x, this page also includes a **Cluster** subpage, which contains the **Dynamic Connections** table as well as the **Active Connection** and **Dynamic Polling IP** parameters.

### Inputs/Outputs

This page contains the **Inputs** and **Outputs** tables, which contain information about the respective inputs and outputs.

### Labels

This page contains the **Matrix Labels** table, which contains label information.

## Notes

Range 1.0.5.x includes the implementation of Dual Controller functionality. Specifically, the main connection dynamically switches in case of a loss of the current connection with one of the devices in the cluster. This range requires DataMiner version **10.3.11.0 - 13456** or higher.
