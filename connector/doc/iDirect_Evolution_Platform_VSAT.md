---
uid: Connector_help_iDirect_Evolution_Platform_VSAT
---

# iDirect Evolution Platform VSAT

The iDirect Evolution Platform VSAT connector can be used to collect data from the iDirect Evolution Platform. 
This platform is an IP-based satellite communication system, with a product line consisting of a universal hub and network management system. 
It is comprised of a series of line cards, operating software and a portfolio of both dedicated and dual-mode remotes.

## About
In elements using this connector, all information about an iDirect NMS is retrieved from MySQL databases and displayed accordingly. All iDirect installations consist of two databases (schemas): "nms" with all the configuration data, and "nrd_archive" with all the events and statistics. 
Depending on the size of the system, these databases can be placed on one or multiple MySQL servers, each one with a different IP address. IP addresses and credentials for access to the databases should be provided in the Database Configuration table on the Configuration page of the element. 
For more information, refer to the "Configuration" section.

The connector also uses data from the Skyline EPM Platform VSAT CMDB, which contains proprietary information about the circuits deployed through the user's satellite network, with customer specific data. This database is queried and provisioned by elements running the Skyline EPM Platform VSAT CMDB protocol (1 per DMA), 
which will generate provisioning files with the necessary circuit information. Elements running the iDirect Evolution Platform VSAT will retrieve the necessary information from the corresponding provisioning file and handle it accordingly.

The connector supports the triggering and clearing of tickets from the system by generating DataMiner information events.  These are generated off the event tables mainly but can also be triggered off the entity tables.

The protocol contains a mechanism to obtain unique numeric IDs for higher level entities used in the EPM solution, but also is completely functional decoupled from EPM.  This functionality can be toggled on and off (EPM Lite) from the configuration page. 
If the connector is configured to use EPM, it will export CSV files for each type of entity that needs to have IDs assigned, and will import the corresponding CSV files with the responses from the EPM manager. 

As this is a virtual connector, no data traffic will be shown in the Stream Viewer.

### Version Info


|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Rewrite of Initial Version		|-         |-         |


### System Info


|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Additional settings need to be specified in the Database Configuration table on the Configuration page of the element. All iDirect databases containing the data that must be polled need to be added in this table:
Rows can be added/deleted in the table via the right-click menu.
For each iDirect hub, exactly one config database and one or more statistics databases must be specified. Even when the config and statistics database have the same IP address, two entries need to be added to the table.
For each database, the Server IP address, Username and Password must be specified. In addition, you have to indicate whether the database contains configuration or statistics (archive) data. Database polling can be enabled or disabled for each entry, and the polling interval can be configured as well.
The DB Hub ID column indicates which iDirect NMS the database belongs to. You can enter the Hub ID yourself, but keep in mind that each hub must have a unique ID, and all databases that belong to the same iDirect hub must have the same ID.
The NMS Name has to be entered in order for the connector to do any subsequent logic related to the NMS (such as aggregation at that level).
In order to obtain unique numeric IDs for entities used in the EPM aggregation process, the following settings need to be specified:
On the configuration page the EPM option must be enabled and the EPM Manager must be present on the system.
On the Collector Setup page, a path must be provided for the import/export of CSV files with ID requests, and toggle buttons for both processes must be enabled.
The collector's agent id / element id must be registered to the EPM collector registration.

### Redundancy

There is no redundancy defined.



## How to use

### General
The **General** page contains general information on the system, such as the number of Active Remotes, Inactive Remotes, Active Networks, Hub Forward and Hub Return.

### Remotes
The **Remotes** page contains the Remotes overview table with specific metrics for all the remote terminals present in the system.

#### Remotes Events
The **Remotes Events** subpage displays the details of all the alarms in the system related to the remotes.

#### Vlan Status
The **Vlan Status** subpage displays the details of all the Vlan and Vrrp events related to the remotes.

#### Remotes Netmodem
The **Remotes Netmodem** subpage is a mapper table tracking the current roaming network status on different remotes in the system.

#### Remotes MODCOD
The **Remotes Modcod** subpage is a table tracking the modcod data of the remotes on the system.

### Circuits
The **Circuit** page displays the Circuits Overview table, which contains config and stats data related to the circuits (with a "circuit" being the network part of the system that resides at the customer site). 
The circuit is considered the bottom entity on the topology chain and is used to aggregate data to the higher entities if EPM functionality is enabled.

### Hub Network
The **Hub Network** page contains the Hub Network Overview table, with config and stats information for the networks present in the system.

### Hub Forward
The **Hub Forward** page contains the Hub Forward Overview table with specific data for the Hub Forward entities.

### Hub Return
The **Hub Return** page contains the following tables:
	**Hub Return Overview** Contains config and stats data for the Hub Return entities
	**Hub Return Carriers** Contains config and stats data for the individual carriers part of a Hub Return.

### Linecards
The **Linecards** page contains the Linecards table with config and stats data for each linecard netmodem on the system.  These linecards are modular electronic circuits designed to fit on a separate printed circuit board (PCB) and interface with a telecommunications access network.

#### Linecard Events
The **Linecard Events** page contains detailed information on each alarm related to the linecards.

### Protocol Processors
The **Protocol Processors** page contains the Protocol Processor Blades table with config and stats data for each server.

#### PP Events
The **PP Events** page contains detailed information for each Protocol Processor related event.

### Chassis
The **Chassis** page contains the Chassis table with config and stats data for each chassis.

#### Chassis Events
The **Chassis Events** page contains detailed information for each alarm related to the Chassis

### Configuration
The **Configuration** page contains the Database Configuration table which stores the required settings for each database being polled by the SQL queries to collect Config, Statistics, and Event data. This page contains the EPM toggle button on the top which enables or disables EPM integration.

#### DB Polling Config
This page allows you to **enable or disable polling** of each data type (Config, Stats, and Events) as well as set the intervals of when the data should be polled.

#### DB Polling Status
This page shows the **metrics** of the polling of each data type (Config, Stats, and Events). These metrics include Status and Execution Time.  There are also buttons located on this page to force the polling of the three different types regardless of the set interval.

#### Auto Clear
This page allows the configuration of the Events Tables. This configuration allows the max days an event stays on the table after being cleared, the total amount of events allowed to be held on the table, and how often the clean-up logic should run. 
You can force the clean-up logic using the Apply button. There is also a clear all button which clears all the events on every **Event** table.

#### Vlan Config
This page allows the configuration of cleanup logic of the Vlan Event table located on the **Vlan Status** page.

### Collector Setup
This page contains all the settings to manage the file handling mechanisms.  These files are the Id files from the EPM which are exported and imported from a specified path, and the CMDB files which are also imported and exported from a specified path. 
The **Directory Type** toggle button allows the user to specify if the file path is located locally on the dma or from a remote location.
The **Entity Removal** Section on the bottom right allows the configuration of how long a circuit with the state of removed(no longer polled on the system) is retained for trend and data purposes.
