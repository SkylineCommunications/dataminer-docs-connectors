---
uid: Connector_help_TPC_Single_Point_of_Failure_Detector
---

# TPC Single Point of Failure Detector

The **TPC Single Point of Failure Detector** can be used to execute queries to a MSSQL database and display the query results. Also, it can be used to create DCF connections.

## About

This connector is a virtual connector developed to execute queries on demand. It retrieves data from the query inserted in the corresponding tables. Also, there are some tables that are manually filled in by the user and used to search for specific data and add DCF connections.

### Version info

| Range     | Key Features     | Based on     | System Impact     |
|-----------|------------------|--------------|-------------------|
| 1.0.0.x   | Initial version  | -            | -                 |

### Product info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   |                        |

### System info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | Yes                 | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

To configure the element using this connector, go to the **Configuration** page, then fill in the **Server Address**, **Database Name**, **User Name**, and **Password**.

Via the **Test Connection** page button, you can check if the connection has been established. Click the **Connect** button and then check the **Connection Result** field.

## How to use

Aside from the **Configuration page**, which contains the connection parameters mentioned above, this connector has the pages described below.

The **Devices**, **Switches**, and **Interfaces** pages contain the data **Execute State Query**, **Query Error Message**, **Query Rows Read**, **Query Last Updated**, as well as a button to execute the query and the table with the data of the executed query.

The subpage **Device Types** contains a data table with the columns **Device type name**, **Protocol Name** (protocol to be used for this specific device type), **Device Name Format** (describes the format of the Device Name), **Element Name Format** (format of the element we then need to look for), and **Type** (Exact Match, Wildcard Match, Regex Match). You can add, edit, end delete rows using the right-click menu of the table.

The subpage **Interface Lookup Table** contains a data table with the columns **Protocol** (name of the protocol in DataMiner), **Database Port format** (the format specifying the port in the Database), **DCF Interface format** (the format for the DCF interface in the Element), and **Type** (Ignore: the interface will not be used, Exact Match, Wildcard Match, Regex Match). Here too you can add, edit, and delete rows using the right-click menu of the table.

The **Connections** page contains the **DCF Connection Table**, which is used to populate DCF connection between the two listed elements. The table will consist of the following columns:

- **From Element**: The element name of the device.
- **From Port**: The DCF Interface from the device from which the connection is created.
- **To Element**: The element name of the switch to connect to.
- **To Port**: The DCF interface of the switch to connect to.

Currently, this table should be filled in by the user (rows can be added, edited, and deleted via the right-click menu). It is possible to create DCF connection for individual rows by clicking on Commit connection in a specific row, or to create connections for all rows for which no connection was previously created. Also, it is possible to export and import the data of this table in CSV format.

### Examples

Device Type (Regex match) example:

- Device Name = 'VGW-705'
- Element Name = 'Imagine SNP VGW705'
- Device Name Format: \[1\]-\[2\]
- Element Name Format: Imagine SNP \[1\]\[2\]

## DataMiner Connectivity Framework

DataMiner Connectivity Framework is supported from initial version (1.0.0.x range).

### Connections

#### External Connections

For each row defined in the DCF Connections table described above, it is possible to create a DCF connection if the data is valid (if elements and interfaces exist).
