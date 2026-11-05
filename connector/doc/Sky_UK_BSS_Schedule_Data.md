---
uid: Connector_help_Sky_UK_BSS_Schedule_Data
---

# Sky UK BSS Schedule Data

## About

The **Sky UK BSS Schedule Data** connector will show the Schedule Data found in the predefined table from the database.

When the connection information is entered correctly, the TX_MONITOR_VIEW table will be loaded every hour (adjustable with **Timer base**) from the Oracle database. This connector uses a virtual connection to poll the data from the database and an HTTP connection to poll the system list from VICC API. It will generate child elements (DVEs) for each bus, according the system that is configured (see "Exported Connectors" below). The table data is filtered by bus and showed in the corresponding DVE.

### Version Info

| Range     | Description                                                                       | DCF Integration     | Cassandra Compliant     |
|------------------|------------------------------------------------------------------------------------|---------------------|-------------------------|
| 1.0.0.x          | Initial version.                                                                   | No                  | Yes                     |
| 1.0.1.x          | Overview table, less information for SLElement and less data polled from database. | No                  | Yes                     |

### Exported Connectors

| Exported Connector                                                                            | Description                                                             |
|--------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| [Sky UK BSS Schedule Data - Bus](xref:Connector_help_Sky_UK_BSS_Schedule_Data_-_Bus) | Shows the current event data from TX_MONITOR_VIEW for that specific bus. |

## Installation and Configuration

### Creation

#### Virtual Connection

This connector uses a virtual connection, for which no input is required during element creation

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device, e.g., *bcam.broadcast.bskyb.com*.
- **IP port**: The IP port of the device, e.g., *80*.
- **Bus address**: This should consist of the **Automation System** to monitor. If a proxy server needs to be bypassed, please specify *byPassProxy*. For example, *byPassProxy;SYSTEM1*.

## Usage

### General

This page shows the parameters related to the DVEs exportation:

The **System** parameter shows which system this element is monitoring.

The **Buses Table** shows a table with every different buses detected in TX_MONITOR_VIEW, along with their **Polling Mode** (can on ON or Off), **System Name**, and **Custom Name**. The buses with Polling Mode ON are listed in the Enabled Buses table. Their data will be exported to a DVE with a name matching the Custom Name column.

The **Enabled Buses** table shows all the buses that will be exported as DVEs, with their System Name, DVE ID, internal ID in DataMiner, Custom Name (which will be the DVE name), and Status. The Status value depends on whether the current event in the schedule has a type equal to "SUSP".

The **Automatic Removal** toggle button allows the user to configure if the DVEs will be automatically deleted when Polling Mode is set to OFF or if they will just be flagged as *Removed* in the DVE Status (Enabled Buses) column and can be removed afterwards.

Several action buttons are also available:

- **Enable All System DVEs** will set **Polling Mode** to *ON* for all the buses where **System Name** matches the **System** configured on this element and generate the DVEs, except for buses that are included in more than one system.

- **Remove All System DVEs** will set **Polling Mode** to *Off* for all the buses where **System Name** matches the **System** configured on this element and delete the DVEs, except for buses that are included in more than one system.

- **Delete All Removed DVEs** will delete all the DVEs that have the *Removed* DVE Status.

Please note that buses that are included in **more than one system** need to be controlled by their **Polling Mode** toggle button. Actions executed by the Enable/Remove All System DVEs will not affect these buses.

### Database Settings

This page contains the configuration parameters Database Name, Server IP, Port, User Name and Password. These are needed to connect to the Oracle database.

For Database Name, there is a discrete value named *Server=Dedicated*, which will drop the SID from the connection string and add *SERVER=DEDICATED* to *CONNECT_DATA*.

There are also several parameters available related to the polling mechanism and an action button:

- **DataBase State**: Shows the state of the communication with the database (*Disabled*, *Finished*, *Polling*, or *General Error*).

- **DataBase Message**: Shows a message when DataBase State is *General Error*.

- **Polling State**: Shows if the polling mechanism is *Enabled* or *Disabled*.

- **Update**: This action button will poll the database when clicked.
