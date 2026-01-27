---
uid: Connector_help_Verimatrix_RTES_Pair_Technical
---

# Verimatrix RTES Pair

## About

With this connector, you can monitor a redundant pair of **Verimatrix RTES** devices using SNMP.

The Verimatrix RTES Pair connector monitors a redundant pair of Verimatrix RTES devices. The **two SNMP connections** are used to connect to the two RTES devices. Through **HTTP SOAP** communication, the connector also allows the user to retrieve the names and key times of the channels that are defined in an Oracle database.

### Exported connectors

| Exported Connector                                                                   | Description                           |
|--------------------------------------------------------------------------------------|---------------------------------------|
| [Verimatrix RTES Pair - DVE](xref:Connector_help_Verimatrix_RTES_Pair_-_DVE)         | 2 DVE elements, primary and secondary |


## Installation and configuration

### Creation

The **Verimatrix RTES Pair** has two SNMP connections. The first is to connect to the **A RTES** device, the second to connect to the **B RTES** device. The IP for those connections needs to be configured during creation of the element.

The **Verimatrix RTES Pair** also has an optional connection to an Oracle database which is handled outside of the scope of the element's settings. The settings for this communication, if opted for, can be done in the **Channel Performance**'s Sub-Page, **Database Settings**.

**SNMP Connection - Server A**:

- **IP address/host**: The polling IP of the main device, e.g. *10.11.12.13.*
- **Port number**: The port of the connected device, by default *161*
- **Get community string**: The community string in order to read from the device. The default value is *public*.
- **Set community string**: The community string in order to set to the device. The default value is *private.*

**SNMP Connection - Server B**:

- **IP address/host**: The polling IP of the secondary device, e.g. *10.11.12.13.*
- **Port number**: The port of the connected device, by default *161*
- **Get community string**: The community string in order to read from the device. The default value is *public*.
- **Set community string**: The community string in order to set to the device. The default value is *private.*

**Oracle Database Connection (configurable under Channel Performance > Database Settings)**:

- **IP Database**: The IP of the Oracle database connection, e.g. *10.11.12.13.*
- **Port Database**: The port of the Oracle database connection, e.g. *161*
- **Instance**: The instance of the table with the required information in the Oracle database.
- **Username**: The Username used to access the Oracle database.
- **Password**: The Password used to access the Oracle database.


## Usage (starting from version 2.0.3.X)

### General Page

This page displays system information, current status and general statistics of both connected devices.

### RTES Page

This page contains the **RTES Table**, listing the RTES devices' information that will be exported as the two seperate DVEs under the view of the parent element, as well as the **Connection Health** table, which displays the current status and information of the DCF connections with the external Network Switch elements.

### Channel Performance Page

This page contains tables with information on the channels of each RTES device.
In addition, the **Database Settings** and **SNMP Channel Information** buttons open a window where you can, respectively, query additional channel information to an Oracle database, or see the raw SNMP Channel information coming from the SNMP table of the devices.

#### Database Settings Sub-Page
Here it is possible to query additional information to an Oracle database, including Channel Names and Key Times. For these to be retrieved successfully, you need to specify the IP of the database, the instance of the table, the username and the password before doing any requests to the database.

#### SNMP Channel Information Sub-Page
In this sub-page it is possible to see the raw SNMP table Channel information from the RTES devices before being processed into the Channel Performance table.

### Channel Health Page

This page contains a table with the bit rate of each channel for both devices, and shows whether the channel bitrate is between the **Minimum** and **Maximum Rate** defined on the **Stream Settings** page, if that channel's Stream Type is defined. If the rate of a channel is outside of the expected boundaries for its defined Stream Type, it will be considered as a Faulty channel for that server. If that is the case, it will add its Weight Factor to the total Error Value of that server, which is used to determine the Server Preference used for redundancy.

This page also displays the current server preference, and both health and timeout status of each server. Additionally, there is a Sub-Page button which will open a window to define and configure the Stream Types used to label each channel's expected rates.

#### Stream Settings Sub-Page

On this sub-page, you can create, edit and delete information about a Stream Type. The configurable values are the **Minimum Rate**, **Maximum Rate** and **Weight Factor**.
- Minimum Rate: Defines the expected Minimum Rate for a channel with the declared Stream Type.
- Maximum Rate: Defines the expected Maximum Rate for a channel with the declared Stream Type.
- Weight Factor: Defines the Error Value associated to a deviation of the rate for a channel with the declared Stream Type, representing the weight for redundancy to consider for the deviation when evaluating Server Preference.


## Usage (version 2.0.2.X and below)

### General Page

This page displays general information and system information on both devices.

### Stream Settings Page

On this page, you can configure the type of stream, and configure some key values, such as the **Minimum Rate**, **Maximum Rate** and **Weight Factor**.

### Channel Performance Page

This page contains tables with information on the channels of each RTES device.

In addition, the **Channel Names** page button opens a window where you can get the channel names. These are retrieved using a query on an Oracle database. To retrieve the channel names, you need to specify the IP of the database, the instance of the table, the username and the password.

### Channel Health Page

This page contains a table with the bit rate of each channel for both devices, and shows whether the channel bitrate is between the **Minimum** and **Maximum Rate** defined on the **Stream Settings** page for that type of stream.

The page also includes information about the communication status of each device, and a parameter that indicates which is the preferred device.

### SNMP Pages

This page contains two tables, which display the RTE indexes.

### RTES

This page contains the **RTES Table**, listing the RTES devices.
