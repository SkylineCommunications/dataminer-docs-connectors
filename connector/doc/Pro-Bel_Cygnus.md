---
uid: Connector_help_Pro-Bel_Cygnus
---

# Pro-Bel Cygnus

This connector allows you to monitor and configure the Pro-Bel Cygnus routing system, using smart-serial communication (with two connections set up as redundant polling) or SNMP communication.

## About

### Version Info

| Range   | Description          | DCF Integration | Cassandra Compliant |
|---------|----------------------|-----------------|---------------------|
| 1.0.0.x | Initial version      | No              | Yes                 |
| 2.0.0.x | Smart-serial version | No              | Yes                 |
| 3.0.0.x | SNMP version         | No              | Yes                 |

### Product Info

| Range   | Supported Firmware Version |
|---------|----------------------------|
| 1.0.0.x | -                          |
| 2.0.0.x | -                          |
| 3.0.0.x | -                          |

## Configuration

### Configuration with Serial Connections

#### Serial Connection - Main

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: 38400
  - **Databits**: 8
  - **Stopbits**: 1
  - **Parity**: Even
  - **FlowControl**: *No*

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: 1

#### Serial Connection - Secondary

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: 38400
  - **Databits**: 8
  - **Stopbits**: 1
  - **Parity**: Even
  - **FlowControl**: *No*

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: 1

### Configuration with SNMP Connection

#### SNMP Main connection

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: 161
- **Get community string**: public
- **Set community string**: private

## How to Use

### Version with Serial Connections

#### Matrix

This page gives an overview of the current matrix configuration. The number of inputs and outputs can be configured in the **Number of Inputs** and **Number of Outputs** parameters, respectively.

The Output Table gives an overview of which input is connected to which output.

#### MON Overview

The **Set MON Name** parameter can be used to add an entry to the **MON Overview** table. Once an entry has been added to the **MON Overview** table, the **Output Table** will be polled.

#### Advanced

This page allows you to set advanced switching using the **Advanced Switching** parameter.

#### Matrix Status

On this page, you can find an overview of the crosspoints (**Crosspoints**), the crosspoints buffer (**Crosspoints Buffer**), and status information (**Status Information** and **Communication Status**).

### Version with SNMP Connection

### General

This page shows the general information of the device. It displays its status and name.

### Matrices

This page displays the Matrices Table.

### Levels

This page displays the Levels Table. The format of the index is {Matrices Index}.{Levels ID}.

### Sources

This page displays the Sources Table. The format of the index is {Levels Index}.{Sources ID}.

The display name can be configured in the format **Source Index**.**Choice**. This choice can be either the alternative name, a 4-character name, an 8-character name, a 12-character name, or a 16-character name.

The Audio Modify can also be configured on the table, and its respective enabled and lock state that are used for in the Matrix.

#### Source Association

This page displays the Source Association Table and the Source Association Sources.

#### Source Settings

On the Sources Table, there is a display name column to identify each row. The format of this display name is "**Source Index**.**Choice**".
The **Choice** is configurable in this page to either use the alternative name, 4 character name, 8 character name, 12 character name, or 16 character name.
The default configuration uses the 16 character name.

### Destinations

This page displays the Destinations Table. The format of the index is {Levels Index}.{Destinations Id}.\
The display name can be configured in the format **Destination Index**.**Choice**. This choice can be either the alternative name, a 4-character name, an 8-character name, a 12-character name, or a 16-character name.

The routed source can also be configured on the table, and its respective enabled and lock state that are used for in the Matrix.

#### Destination Settings

The display name can be configuration of the Destinations Table display name. It uses the format **Destination Index**.**Choice**. This choice can be either the alternative name, a 4-character name, an 8-character name, a 12-character name, or a 16-character name. The default configuration uses the 16-character name.

### Matrix

This page shows the matrix, an overview of the crosspoints of the destinations and sources.

The sources of each destination can be configured on this matrix, and destinations and sources can be locked.
