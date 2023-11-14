---
uid: Connector_help_ETL_Systems_NGM-21
---

# ETL Systems NGM-21

This connector displays information related to the **ETL Systems NGM-21** device.

This connector uses two interfaces to communicate with the NGM-21 device. The SNMP interface is used to retrieve information regarding the chassis temperature and the status of the fans, and the serial interface is used to execute the remaining commands.

## About

### Version Info

| Range              | Key Features                                                                 | Based on | System Impact |
|--------------------|------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x            | Initial version.                                                             | -        | -             |
| 1.0.1.x [SLC Main] | Labels and locks are retrieved via serial communication instead of via SNMP. | 1.0.0.8  | None. The major change was required because unused table columns have been removed from the Output Settings table. |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |
| 1.0.1.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |
| 1.0.1.x | No              | Yes                 | -                 | -                   |

## Creation

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP Address/host**: The polling IP of the device, e.g. *10.145.1.12*.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string required to read from the device. The default value is *public*.
- **Set community string**: The community string required to set to the device. The default value is *public*.

#### Serial Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **Type of port:** TCP/IP.
- **IP address/host**: The polling IP or URL of the destination, e.g. *10145.1.12*.
- **IP port**: The port of the destination, e.g. *13000*.
- **Timeout of a single command:** 2500 ms (minimum).

## Usage

### Main View Page

This page contains the device matrix.

### General Page

This page displays generic parameters, such as the version and IP address.

### Alarm Page

This page displays the device status, such as temperatures, fan speeds, and communication state.

### Configuration Page

On this page, you can configure the matrix size.
