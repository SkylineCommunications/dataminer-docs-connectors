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

## Configuration

### Connections

The **Verimatrix RTES Pair** has two SNMP connections. The first is to connect to the **A RTES** device, the second to connect to the **B RTES** device. The IP for those connections needs to be configured during creation of the element.

The **Verimatrix RTES Pair** also has an optional connection to an Oracle database which is handled outside of the scope of the element's settings. You can configure the settings for this connection on the **Channel Performance** > **Database Settings** page of the connector.

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

## Usage (starting from version 2.0.3.x)

### General Page

This page displays system information, current status and general statistics of both connected devices.

### RTES Page

This page contains the **RTES Table**, listing the RTES devices' information, which will be exported to two separate DVEs under the view of the parent element, as well as the **Connection Health** table, which displays the current status and information of the DCF connections with the external network switch elements.

### Channel Performance Page

This page contains tables with information on the channels of each RTES device.

In addition, the **Database Settings** and **SNMP Channel Information** buttons open the following subpages:

- **Database Settings**: Allows you to query additional information from an Oracle database, including Channel Names and Key Times. For these to be retrieved successfully, before doing any requests to the database, you need to specify the IP of the database, the instance of the table, the username and the password.
- **SNMP Channel Information**: Displays the raw SNMP table Channel information from the RTES devices before it is processed into the Channel Performance table.

### Channel Health Page

This page contains a table with the bit rate of each channel for both devices, and shows whether the channel bitrate is between the **Minimum** and **Maximum Rate** defined on the **Stream Settings** subpage, if that channel's stream type is defined. If the rate of a channel is outside of the expected boundaries for its defined stream type, it will be considered a faulty channel for that server. If that is the case, its weight factor will be added to the total error Value of that server, which is used to determine the server preference used for redundancy.

This page also displays the current server preference, and both health and timeout status of each server.

Additionally, a page button opens the **Stream Settings** subpage, where you can configure the stream types used to label each channel's expected rates. The following parameters can be configured for each stream type:

- **Minimum Rate**: Determines the expected minimum rate for a channel with the declared stream type.
- **Maximum Rate**: Determines the expected maximum rate for a channel with the declared stream type.
- **Weight Factor**: Determines the error value associated with a deviation of the rate for a channel with the declared stream type, representing the weight for redundancy to consider for the deviation when evaluating server preference.

## Usage (version 2.0.2.x and lower)

### General Page

This page displays general information and system information on both devices.

### Stream Settings Page

On this page, you can configure the type of stream, and configure some key values, such as the **Minimum Rate**, **Maximum Rate**, and **Weight Factor**.

### Channel Performance Page

This page contains tables with information on the channels of each RTES device.

In addition, the **Channel Names** page button opens a window where you can get the channel names. These are retrieved using a query on an Oracle database. To retrieve the channel names, you need to specify the IP of the database, the instance of the table, the username and the password.

### Channel Health Page

This page contains a table with the bit rate of each channel for both devices. It shows whether the channel bitrate is between the **Minimum** and **Maximum Rate** defined on the **Stream Settings** page for that type of stream.

The page also includes information about the communication status of each device, and a parameter that indicates which is the preferred device.

### SNMP Pages

This page contains two tables, which display the RTE indexes.

### RTES

This page contains the **RTES Table**, listing the RTES devices.
