---
uid: Connector_help_Pro-Bel_Cygnus
---

# Pro-Bel Cygnus

This connector allows to monitor and configure the the Pro-Bel Cygnus routing system.

## About

This connector allows to monitor and configure the Pro-Bel Cygnus routing system, using smart-serial communication. The connector has two smart-serial connections which are set up as redundant polling.

### Version Info

| **Range** | **Description**      | **DCF Integration** | **Cassandra Compliant** |
|------------------|----------------------|---------------------|-------------------------|
| 1.0.0.x          | Initial version      | No                  | Yes                     |
| 2.0.0.x          | Smart Serial version | No                  | Yes                     |
| 3.0.0.x          | SNMP version         | No                  | Yes                     |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | -                           |
| 2.0.0.x          | -                           |
| 3.0.0.x          | -                           |

## Installation and configuration

### Creation

#### Serial connection - Main

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

#### Serial connection - Secondary

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

## Usage - SERIAL

### Matrix

This page gives an overview of the current matrix configuration. The number of inputs and outputs can be configured in the **Number of Inputs** and **Number of Outputs** parameters, respectively.

The Output Table gives an overview of which input is connected to which output.

### MON Overview

The **Set MON Name** parameter can be used to add an entry to the **MON Overview** table. Once an entry has been added to the **MON Overview** table, the **Output Table** will be polled.

### Advanced

This page allows to set advanced switching using the **Advanced Switching** parameter.

### Matrix Status

On this page an overview is given of the crosspoints (**Crosspoints**), the crosspoints buffer (**Crosspoints Buffer**), and status information (**Status Information** and **Communication Status**).

## Usage - SNMP

### General
This page shows the general information of the device. It displays its status and name.

### Matrice
This page shows an overview of the Matrice Table.

### Levels
This page shows an overview of the Levels Table. The format of the Index is {Matrice Index}.{Levels Id}.

### Sources
This page shows an overview of the Sources Table. The format of the Index is {Levels Index}.{Sources Id}.\
The display name can be configured in the format of **Source Index**.**Choice** which choice can be either the alternative name, 4 character name, 8 character name, 12 character name, or 16 character name.

The Audio Modify can also be configured on the table, and its respective enabled and lock state that are used for in the Matrix.

#### Source Association
This page shows an overview of the Source Assiociation Table and the Source Association Sources.

#### Source Settings
This page allows the 
The display name can be configuration of the Sources Table display name. It is formatted in the format of **Source Index**.**Choice** which choice can be either the alternative name, 4 character name, 8 character name, 12 character name, or 16 character name. The default configuration uses the 16 character name choice.

### Destinations
This page shows an overview of the Destinations Table. The format of the Index is {Levels Index}.{Destinations Id}.\
The display name can be configured in the format of **Destination Index**.**Choice** which choice can be either the alternative name, 4 character name, 8 character name, 12 character name, or 16 character name.

The routed source can also be configured on the table, and its respective enabled and lock state that are used for in the Matrix.

#### Destination Settings
This page allows the 
The display name can be configuration of the Destinations Table display name. It is formatted in the format of **Destination Index**.**Choice** which choice can be either the alternative name, 4 character name, 8 character name, 12 character name, or 16 character name. The default configuration uses the 16 character name choice.

### Matrix
This page shows the Matrix, an overview of the crosspoints of the destinations and sources.\
The sources of each destination can be configured on this Matrix, as well as locking of destinations and sources.

