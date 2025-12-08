---
uid: Connector_help_Linux_Platform
---

# Linux Platform

With this connector, you can monitor servers running Linux OS with SSH or with SNMP.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|---------|----------------|------------|------------------|
|1.0.0.x|Initial version.| - | - |
|1.1.0.x|Added version compatibility.| - | - |
|1.1.1.x|Added SNMP connection.| - | - |
|2.0.0.x| Changed the layout of the connector. The connector can now poll the data using SSH or SNMP. If one of the connections fails, it will use the other connection to poll the data.| - |After version 1.1.1.x, the connection type changes from serial to SNMP, which means that existing elements will need to be re-created when you update to the latest version.|
|2.0.1.x |Added CLI Table.| - | CLI Table uses context menu with NuGet.|
|2.0.2.x [SLC Main] | - Information from Interfaces table fixed and bit rates updated methods implemented.<br>- Tooltip of parameter Data Type Mode improved.<br>- Available Disk Space % (percentage) added to Disks table.| 2.0.1.15 | - NuGets for rate calculation updated.<br>- Interfaces table layout and content changed.|

### Product Info

| Range | Supported Firmware |
|-------|--------------------|
|1.0.0.x| Not applicable     |
|1.1.0.x| Not applicable     |
|1.1.1.x| Not applicable     |
|2.0.0.x| Not applicable     |
|2.0.1.x| Not applicable     |
|2.0.2.x| Not applicable     |

### System Info

| Range | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-------|---------------------|-------------------------|-----------------------|-------------------------|
|1.0.0.x| No                  | Yes                     | -                     | -                       |
|1.1.0.x| Yes                 | Yes                     | -                     | -                       |
|1.1.1.x| Yes                 | Yes                     | -                     | -                       |
|2.0.0.x| No                  | Yes                     | -                     | -                       |
|2.0.1.x| No                  | Yes                     | -                     | -                       |
|2.0.2.x| No                  | Yes                     | -                     | -                       |

## Configuration

### Connections - Range 1.0.0.x - 1.1.1.x

#### Serial connection

- **IP address/host:** The polling IP of the Linux platform.
- **IP port:** The IP port of the device.

### Connections - Range 2.0.0.x - 2.0.1.x

#### SNMP connection

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13.*
- **Port number:** The port of the connected device, by default 161.
- **Get community string:** The community string in order to read from the device, by default *public*.
- **Set community string:** The community string in order to set to the device, by default *private*.

#### SERIAL connection

- **IP address/host:** The polling IP of the Linux platform.
- **IP port:** The IP port of the device, by default *22* (SSH).

### Configuration SSH

On the **General page**, click **Security** to enter the Login and Password. Then click the **Login** button to start the communication.

For range **2.0.0.x** or higher, on the **General page**, click **Configuration** to set up the **SSH configuration** and to select the connection type, **SNMP** or **SSH**.

## Usage (Range 2.0.0.x -2.0.1.x)

### General

This page displays general information regarding the Linux platform, such as **Device info**, **Total Processor Load**, **Memory usage**, etc.

The page contains several page buttons:

- **Ping**: Allows you to configure the ping definitions.
- **Load**: Displays load information.
- **Raw CPU**: Displays detailed information on CPU usage.
- **Processor**: Displays processor load information.
- **Configuration**: Allows you to specify the SSH username and password and to choose the connection type.

NOTE: In SSH Mode, the Processor table will use different indexes for each processor, since there is no way to match the indexes with SNMP. This means **switching between SSH and SNMP will lead to loss of alarm and trend data**.

### Task Manager

This page contains the **Task Manager** table, which lists the processes that are active on the server.

Note that if the **Communication Type** is *SSH* (on the Configuration page), the **CPU Load** of a process can exceed 100% if the process uses multiple cores. If a process is multi-threaded, it can use multiple cores simultaneously. For example, if you run a multi-threaded application like a video encoder or a scientific computation tool, it might show 300% CPU load on a quad-core system. This means it is using three cores fully. 200% CPU load means two cores are fully utilized, and so on. The **Normalized CPU Load** column shows the CPU load per process in the range of 0% to 100%.

In addition, the **Process Validation** table allows you to validate whether a given process is still running upon each new polling cycle.
When you add a process to validate, you will be able to select it from a prepopulated list of the current processes.

### Network Info

This page lists the information about the network interfaces.

### Memory Info

This page displays memory information, such as the **Available Physical Memory**, **Total Physical Memory**, and **Memory Usage**.

### Disks Info

This page contains the following tables:

- **Disks**: Displays information on the disks, such as the **Total Size**, **Available Space**, and **Used Percentage**.
- **Disks IO**: Displays the disks' read/write information.

### Software Info

This page displays the **Software Installed** table, which lists the software installed on the server.

### HP/Dell

If the Linux platform is installed on an HP/Dell platform, you can enable **Poll HP Parameters** or **Poll Dell Parameters** to receive specific HP or Dell data.

The following page buttons allow access to additional HP or Dell info:

- **Fan**
- **Power Supply**
- **Temperature**
- **Memory**
- **CPU**
- **Disk**

### Virtual Server

This page displays general information about the virtual server. It also allows you to enable/disable **Poll LVS Parameters** to receive the data in question.

The following page buttons allow access to additional virtual server info:

- **LVS Real Table**
- **Service Table**

## Usage (Range 1.0.0.x - 1.1.1.x)

### General Page

This page displays general information regarding the Linux Platform:

- **Linux Version**
- **Current Time**
- **Uptime**
- **Users**

The page button **Security** can be used to enter the credentials.

### CPU Info

This page displays CPU information.

### Memory Info

This page contains memory information.

### Disk Info

This page displays disk information.

### Process List

This page displays a list of all the processes running on the Linux platform.

With the **Remove Not Running** button, you can remove processes that no longer exist.

### Network Interface Info

This page displays all interfaces and data rates.

### Network Interface Info - Rx

This page displays all interfaces and Rx-related data rates.

### Network Interface Info - Tx

This page displays all interfaces and Tx-related data rates.

### HP/Dell

From version **1.1.1.x** onwards, if the Linux platform is installed on an HP/Dell platform, you can enable **Poll HP Parameters** or **Poll Dell Parameters** to receive specific HP or Dell data.

The following page buttons allow access to additional HP or Dell info:

- **Fan**
- **Power Supply**
- **Temperature**
- **Memory**
- **CPU**
- **Disk**

## DataMiner Connectivity Framework

From version **1.1.0.7** onwards, this connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (for instance a manager).

### Interfaces

#### Dynamic Interfaces

Physical dynamic interfaces:

- The physical dynamic interface is created for the parameter **Network Interface Table** and its interface is **inout**.
