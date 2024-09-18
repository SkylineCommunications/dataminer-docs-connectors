---
uid: Connector_help_iDirect_Evolution_Platform_VSAT
---

# iDirect Evolution Platform VSAT

The iDirect Evolution Platform VSAT connector can be used to collect data from the iDirect Evolution Platform. This platform is an IP-based satellite communication system, with a product line consisting of a universal hub and network management system. It consists of a series of line cards, operating software, and a portfolio of both dedicated and dual-mode remotes.

In elements using this connector, all information about an iDirect NMS is retrieved from **MySQL databases** and displayed accordingly. All iDirect installations consist of two databases (schemas): "nms" with all the configuration data, and "nrd_archive" with all the events and statistics. Depending on the size of the system, these databases can be placed on one or multiple MySQL servers, each one with a different IP address. IP addresses and credentials for access to the databases should be provided in the **Database Configuration** table on the Configuration page of the element (See [Configuration](#configuration) below).

The connector also uses data from the Skyline **EPM Platform VSAT CMDB**, which contains proprietary information about the circuits deployed through the user's satellite network, with customer-specific data. This database is queried and provisioned by elements running the Skyline EPM Platform VSAT CMDB protocol (1 per DMA), which will generate provisioning files with the necessary circuit information. Elements running the iDirect Evolution Platform VSAT will retrieve the necessary information from the corresponding provisioning file and handle it accordingly.

The connector supports the triggering and clearing of **tickets** from the system by generating DataMiner information events. These are mainly generated based on the event tables but can also be triggered base on the entity tables.

The connector contains a mechanism to obtain unique numeric IDs for higher-level entities used in the EPM solution, but it is also completely functional decoupled from EPM. This functionality can be toggled on and off (EPM Lite) on the Configuration page. If the connector is configured to use EPM, it will export CSV files for each type of entity that needs to have IDs assigned, and it will import the corresponding CSV files with the responses from the EPM manager.

As this is a virtual connector, no data traffic will be shown in the Stream Viewer.

## About

### Version Info

| Range              | Features                    | Based on | System Impact |
|--------------------|-----------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Rewrite of initial version. | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Once you have created the element, you will need to configure additional settings in the **Database Configuration** table on the **Configuration** page. All iDirect databases containing the data that must be polled need to be added in this table:

- You can add or delete rows in the table via the right-click menu.
- For each iDirect hub, exactly one config database and one or more statistics databases must be specified. Even when the config and statistics database have the same IP address, two entries need to be added to the table.
- For each database, the **Server IP Address**, **Username**, and **Password** must be specified. In addition, you have to indicate whether the database contains configuration or statistics (archive) data. Database polling can be enabled or disabled for each entry, and the polling interval can be configured as well.
- The **DB Hub ID** column indicates which iDirect NMS the database belongs to. You can enter the Hub ID yourself, but keep in mind that each hub must have a unique ID, and that all databases that belong to the same iDirect hub must have the same ID.
- The **NMS Name** has to be entered in order for the connector to do any subsequent logic related to the NMS (such as aggregation at that level).

In order to obtain unique numeric IDs for entities used in the EPM aggregation process, the following settings need to be specified:

- On the Configuration page, the EPM option must be enabled, and an EPM Manager must be present in the system.
- On the Collector Setup page, a path must be provided for the import/export of CSV files with ID requests, and toggle buttons for both processes must be enabled.
- The collector's Agent ID/element ID must be registered to the EPM collector registration.

## How to use
When you first start up the element make your way to the configuration page. 

### Configuration Page

The **Configuration** page contains the **Database Configuration** table, which stores the required settings for each database that is polled by the SQL queries to collect Config, Statistics, and Event data. This table is a context menu table so you will need to configure the values for each individual database. This includes the Ip Address, Username, and Password. At the top of this page, you can find the **EPM toggle button**, which can be used to enable or disable EPM integration.

This page has several subpages:

- **DB Polling Config**: Allows you to **enable or disable polling** of each data type (Config, Stats, and Events) as well as set the intervals at which the data should be polled.
- **DB Polling Status**: Shows the **metrics** of the polling of each data type (Config, Stats, and Events). These metrics include Status and Execution Time. There are also buttons on this page to force the polling of the three different types regardless of the set interval.
- **Auto Clear**: Allows the configuration of the Events Tables. This configuration includes the maximum number of days an event stays in the table after being cleared, the total number of events allowed in the table, and how often the clean-up logic should run. You can force the clean-up logic using the **Apply** button. There is also a **Clear All** button, which clears all the events in every Event table.
- **Vlan Config**: This page allows the configuration of cleanup logic of the Vlan Event table located on the **Vlan Status** page.

After configuring the databases make your way to the collector setup page. 

### Collector Setup Page

This page contains all the settings to manage the file handling mechanisms. These files are the ID files from the EPM setup, which are exported and imported from a specified path, and the CMDB files, which are also imported and exported from a specified path. If EPM integration is not enabled, then the only thing necessary to configure on this page is the entity removal section detailed below.  This section handles the cleanup of tables for removed entites.

The **Directory Type** toggle button allows you to specify if the file path is located locally on the DMA or in a remote location.

The **Entity Removal** section in the lower right corner allows you to configure how long an entity with the state "removed" (no longer polled in the system) is retained for trend and data purposes.
