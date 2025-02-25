---
uid: Connector_help_HP_ILO_Management_Engine
---

# HP iLO Management Engine

This device is a remote server management processor embedded in the system boards of HPE ProLiant servers and Synergy compute modules. iLO enables the monitoring and control of servers from remote locations. HPE iLO management is a powerful tool that provides multiple ways to configure, update, monitor, and repair servers remotely.

## About

This connector is used to retrieve the required data from the HP iLO Management Engine device.

It uses the REST API to get and set all the associated parameters for this type of device.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| 1.0.0.x [not to be used - no monitoring capabilities due to undocumented API] | Initial version | No | Yes |
| 1.0.1.x **[SLC Main]** | Using the RedFish API - iLO 4 | No | Yes |
| 1.1.0.x **[Obsolete]** | Using the Redfish API - iLO 5 | No | Yes |
| 1.1.1.x **[SLC Main]** | Using the Redfish API - iLO 5 with SNMP polling | No | Yes |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | 2.55                        |
| 1.0.1.x          | 2.55 - iLO 4                |
| 1.1.0.x          | 1.37 - iLO 5                |
| 1.1.1.x          | 1.37 - iLO 5                |

## Installation and configuration

### Creation

#### HTTP Main Connection

This connector uses an HTTP connection and an SNMP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The device API IP Port (default *443*).
- **BusAddress**: The Computer System ID (default: *ByPassProxy*).

#### SNMP Connection

Note: This connection is only available from version 1.1.1.x onwards.

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The device IP port (default *161*).

## Usage

### General

This page displays the general device information, including the **Server Name**, **Product Name**, **UUID**, **Serial Number**, **Product ID**, **System ROM**, **System ROM Date**, **Backup ROM Date**, **System Health**, **Power**, **UID Indicator**, **Date**, **ILO Name**, **License**, **ILO FW Version**, **IP Address**, and **IPV6 Link Local**.

### Active Sessions

This page displays a table with information related to active sessions. The table contains the following columns: **Index**, **User Type**, **User Name,** **User Tag**, and **User IP**.

### Connection Setup

On this page, you can fill in the credentials for the HTTP API polling in the **User Name** and **Password** boxes.

By default, **SNMP polling** is disabled, but you can enable it by toggling the **SNMP Polling** parameter. SNMP polling is used to populate the items and subpages of the **Alarms** page.

### System Information

This page displays contains 9 subpages pages which can be accessed by clicking the following buttons:

- **Software**: Displays the **Software Inventory**, with the following columns: **ID**, **Name**, **Description**, and **Version**. This table can only be polled if the device has the license type **Advanced**. With the **Polling Configuration** toggle button, you can enable or disable the polling of this table.

  Note that the **Software Inventory** function will only work if the **Agentless Management Service** is in the state *Running* (available on the **General** page in the 1.1.0.1 range).

- **Firmware**: Displays the **Firmware Version Info Table**, with the following columns: **Index**, **Firmware Name**, **Firmware Version**, and **Location**.
- **Processors**: Displays the **Processors Table**, with the following columns: **Index**, **Name**, **Status**, **Speed**, **Execution Technology**, **Memory Technology**, **Internal L1 Cache**, **Internal L2 Cache**, and **Internal L3 Cache**.
- **Storage**: Displays a tree structure with the **Controllers**, **Enclosures**, **Physical Drives**, and **Logical Drives**.
- **Network**: Displays a tree structure containing the **Network Adapters Table**, with the following parameters: **Name**, **Description**, **Location**, **Status**, and **Firmware**. Also contains the **Network Adapter Ports Table** as level 1, which has the following columns: **Number, MAC Address, IPV4, IPV6, Status**, and **Team Bridge**.
- **Memory**: Contains two standalone parameters, **Advanced Mode Status** and **Configured AMP Mode**, as well as the **Memory Summary Table**, which contains information regarding each memory board.
- **Power**: Contains information regarding **Power Supplies** and **Power Configurations**.
- **Temperatures**: Displays the **Temperature Table**, with the following parameters: **Sensor**, **Location**, **Status**, **Reading**, **Units**, and **Thresholds**.
- **Fans**: Displays the **Fans Table**, with the following parameters: **Index**, **Location**, **Status**, **Speed**, and **Unit**.

In case some piece of information seems to be missing, first check whether the actual web page of the ILO device does show the missing information.

### Integrated Management Log

This page displays the **Integrated Management Log Table**, which contains the following columns: **Description,** **Severity**, **Last Update**, and **Initial Update**.

Some configuration options are available to manage the table:

- **Clear Log**: Clears the table (only available in the 1.0.0.x and 1.0.1.x range).
- **Refresh**: Forces a refresh of the data in the table.
- **Polling Configuration**: Allows you to set the polling rate of the table to each hour or 5 min.
- **Maximum Number of Entries**: Allows you to limit the total number of rows available in the table.

### iLO Event Log

This page displays the **ILO Event Log Table**, which contains the following columns: **Description**, **Severity**, **Last Update**, **Initial Update**, and **Count**.

Some configuration options are available to manage the table:

- **Clear Log**: Clears the table.
- **Refresh**: Forces a refresh of the data in the table.
- **Polling Configuration**: Allows you to set the polling rate of the table to each hour or 5 min.
- **Maximum Number of Entries**: Allows you to limit the total number of rows available in the table.

### Alarms

The **Alarms** page contains parameters related to the status, health, and condition of various components of the device. The page has several subpages with detailed information about the status of those components.

### Web Interface

This page displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
