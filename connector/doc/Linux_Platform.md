---
uid: Connector_help_Linux_Platform
---

# Linux Platform

With this connector, you can monitor servers running Linux OS with SSH or with SNMP.

## About

### Version Info

|**Range**|**Key Features**|**Based on**|**System Impact** |
|---------|----------------|------------|------------------|
|1.0.0.x|Initial version.| - | - |
|1.1.0.x|Added version compatibility.| - | - |
|1.1.1.x|Added SNMP connection.| - | - |
|2.0.0.x [SLC Main]| Changed the layout of the connector. The connector can now poll the data using SSH or SNMP. If one of the connections fails, it will use the other connection to poll the data.| - |After version 1.1.1.x, the connection type changes from serial to SNMP, which means that existing elements will need to be re-created when you update to the latest version.|
|2.0.1.x|Added CLI Table.| - | CLI Table uses context menu with NuGet.|

### Product Info

| Range | Supported Firmware |
|-------|--------------------|
|1.0.0.x| Not applicable     |
|1.1.0.x| Not applicable     |
|1.1.1.x| Not applicable     |
|2.0.0.x| Not applicable     |
|2.0.1.x| Not applicable     |

### System Info

| Range | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-------|---------------------|-------------------------|-----------------------|-------------------------|
|1.0.0.x| No                  | Yes                     | -                     | -                       |
|1.1.0.x| Yes                 | Yes                     | -                     | -                       |
|1.1.1.x| Yes                 | Yes                     | -                     | -                       |
|2.0.0.x| No                  | Yes                     | -                     | -                       |
|2.0.1.x| No                  | Yes                     | -                     | -                       |

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

## SNMP OIDs implemented (in construction)

|Parameter Name|SNMP Parameter Name (MIB File)|SNMP OID|MIB File|
|--------------|------------------------------|--------|--------|
|System Description|sysDescr|1.3.6.1.2.1.1.1.0|RFC1213-MIB|
|System Uptime|sysUpTime|1.3.6.1.2.1.1.3.0|RFC1213-MIB|
|System Name|sysName|1.3.6.1.2.1.1.6.0|RFC1213-MIB|
|System Location|sysLocation|1.3.6.1.2.1.1.6.0|RFC1213-MIB|
|HR System Uptime|hrSystemUptime|1.3.6.1.2.1.25.1.1.0|HOST-RESOURCES-MIB|
|SNMP Engine Time|snmpEngineTime|1.3.6.1.6.3.10.2.1.3.0|SNMP-FRAMEWORK-MIB|
|Total Processor Load|IaLoad|1.3.6.1.4.1.2021.10.1.3.1|UCD-SNMP-MIB|
|Available Physical Memory|memTotalFree|1.3.6.1.4.1.2021.4.11.0|UCD-SNMP-MIB|
|Total Real Memory|memTotReal|1.3.6.1.4.1.2021.4.5.0|UCD-SNMP-MIB|
|Number of Users|hrSystemNumUsers|1.3.6.1.2.1.25.1.5.0|HOST-RESOURCES-MIB|
|Number of Processes|hrSystemProcesses|1.3.6.1.2.1.25.1.6.0|HOST-RESOURCES-MIB|
|Total Swap Memory|memTotalSwap|1.3.6.1.4.1.2021.4.3.0|UCD-SNMP-MIB|
|Available Swap Memory|memAvailSwap|1.3.6.1.4.1.2021.4.4.0|UCD-SNMP-MIB|
|Available Real Memory|memAvailReal|1.3.6.1.4.1.2021.4.6.0|UCD-SNMP-MIB|
|Memory Buffer|memBuffer|1.3.6.1.4.1.2021.4.14.0|UCD-SNMP-MIB|
|Memory Cached|memCached|1.3.6.1.4.1.2021.4.15.0|UCD-SNMP-MIB|
|System CPU|cpuSystemPercentage|1.3.6.1.4.1.2021.11.10.0|UCD-SNMP-MIB|
|Local Time SNMP|hrSystemDate|1.3.6.1.2.1.25.1.2.0|HOST-RESOURCES-MIB|
|Raw CPU User|ssCpuRawUser|1.3.6.1.4.1.2021.11.50.0|UCD-SNMP-MIB|
|Raw CPU Nice|ssCpuRawNice|1.3.6.1.4.1.2021.11.51.0|UCD-SNMP-MIB|
|Raw CPU System|ssCpuRawSystem|1.3.6.1.4.1.2021.11.52.0|UCD-SNMP-MIB|
|Raw CPU Idle|ssCpuRawIdle|1.3.6.1.4.1.2021.11.53.0|UCD-SNMP-MIB|
|Raw CPU Wait|ssCpuRawWait|1.3.6.1.4.1.2021.11.54.0|UCD-SNMP-MIB|
|Raw CPU Kernel|ssCpuRawKernel|1.3.6.1.4.1.2021.11.55.0|UCD-SNMP-MIB|
|Raw CPU Interrupt|ssCpuRawInterrupt|1.3.6.1.4.1.2021.11.56.0|UCD-SNMP-MIB|
|PID (Task Manager)|hrSWRunIndex|1.3.6.1.2.1.25.4.2.1.1|HOST-RESOURCES-MIB|
|Name (Task Manager)|hrSWRunName|1.3.6.1.2.1.25.4.2.1.2|HOST-RESOURCES-MIB|
|CPU Time (Task Manager)|hrSWRunPerfCPU|1.3.6.1.2.1.25.5.1.1.1|HOST-RESOURCES-MIB|
|Memory Usage (Task Manager)|hrSWRunPerfMem|1.3.6.1.2.1.25.5.1.1.2|HOST-RESOURCES-MIB|
|Status (Task Manager)|hrSystemMaxProcesses|1.3.6.1.2.1.25.4.2.1.7|HOST-RESOURCES-MIB|
|Full Path (Task Manager)|hrSWRunPath|1.3.6.1.2.1.25.4.2.1.4|HOST-RESOURCES-MIB|
|Run Parameters (Task Manager)|hrSWRunParameters|1.3.6.1.2.1.25.4.2.1.5|HOST-RESOURCES-MIB|
|Firmware (Processor)|hrProcessorFrwID|1.3.6.1.2.1.25.3.3.1.1|HOST-RESOURCES-MIB|
|Load (Processor)|hrProcessorLoad|1.3.6.1.2.1.25.3.3.1.2|HOST-RESOURCES-MIB|
|Device Type (Devices)|hrDeviceType|1.3.6.1.2.1.25.3.2.1.2|HOST-RESOURCES-MIB|
|Device Description (Devices)|hrDeviceDescr|1.3.6.1.2.1.25.3.2.1.3|HOST-RESOURCES-MIB|
|Device ID (Devices)|hrDeviceID|1.3.6.1.2.1.25.3.2.1.4|HOST-RESOURCES-MIB|
|Device Status (Devices)|hrDeviceStatus|1.3.6.1.2.1.25.3.2.1.5|HOST-RESOURCES-MIB|
|Device Errors (Devices)|hrDeviceErrors|1.3.6.1.2.1.25.3.2.1.6|HOST-RESOURCES-MIB|
|Index (Load Average Information)|IaIndex|1.3.6.1.4.1.2021.10.1.1|UCD-SNMP-MIB|
|Description \[IDX\] (Load Average Information)|IaNames|1.3.6.1.4.1.2021.10.1.1|UCD-SNMP-MIB|
|Load (Load Average Information)|IaLoad|1.3.6.1.4.1.2021.10.1.3|UCD-SNMP-MIB|
|Name \[IDX\](Software Installed)|hrSWInstalledName|1.3.6.1.2.1.25.6.3.1.2|HOST-RESOURCES-MIB|
|ID (Software Installed)|hrSWInstalledID|1.3.6.1.2.1.25.6.3.1.3|HOST-RESOURCES-MIB|
|Type (Software Installed)|hrSWInstalledType|1.3.6.1.2.1.25.6.3.1.4|HOST-RESOURCES-MIB|
|Index (Disks)|dskIndex|1.3.6.1.4.1.2021.9.1.1|UCD-SNMP-MIB|
|Path \[IDX\] (Disks)|dskPath|1.3.6.1.4.1.2021.9.1.2|UCD-SNMP-MIB|
|Device (Disks)|dskDevice|1.3.6.1.4.1.2021.9.1.3|UCD-SNMP-MIB|
|Total Minimum Space (Disks)|dskMinimum|1.3.6.1.4.1.2021.9.1.4|UCD-SNMP-MIB|
|Minimum Space (Disks)|dskMinPercentage|1.3.6.1.4.1.2021.9.1.5|UCD-SNMP-MIB|
|Total Size (Disks)|dskTotal|1.3.6.1.4.1.2021.9.1.6|UCD-SNMP-MIB|
|Available Space (Disks)|dskAvail|1.3.6.1.4.1.2021.9.1.7|UCD-SNMP-MIB|
|Total Memory Used (Disks)|dskUsed|1.3.6.1.4.1.2021.9.1.8|UCD-SNMP-MIB|
|Memory Used (Disks)|dskPercent|1.3.6.1.4.1.2021.9.1.9|UCD-SNMP-MIB|
|Inodes Used (Disks)|dskPercentNode|1.3.6.1.4.1.2021.9.1.10|UCD-SNMP-MIB|
|Total Size Low (Disks)|dskTotalLow|1.3.6.1.4.1.2021.9.1.11|UCD-SNMP-MIB|
|Total Size High (Disks)|dskTotalHigh|1.3.6.1.4.1.2021.9.1.12|UCD-SNMP-MIB|
|Available Space Low (Disks)|dskAvailLow|1.3.6.1.4.1.2021.9.1.13|UCD-SNMP-MIB|
|Available Space High (Disks)|dskAvailHigh|1.3.6.1.4.1.2021.9.1.14|UCD-SNMP-MIB|
|Total Memory Used Low (Disks)|dskUsedLow|1.3.6.1.4.1.2021.9.1.15|UCD-SNMP-MIB|
|Total Memory Used High (Disks)|dskUsedHigh|1.3.6.1.4.1.2021.9.1.16|UCD-SNMP-MIB|
|Index (Disk IO)|diskIOIndex|1.3.6.1.4.1.2021.13.15.1.1.1|UCD-DISKIO-MIB|
|Device (Disk IO)|diskIODevice|1.3.6.1.4.1.2021.13.15.1.1.2|UCD-DISKIO-MIB|
|Read (Disk IO)|diskIONRead|1.3.6.1.4.1.2021.13.15.1.1.3|UCD-DISKIO-MIB|
|Written (Disk IO)|diskIONWritten|1.3.6.1.4.1.2021.13.15.1.1.4|UCD-DISKIO-MIB|
|Reads Accesses (Disk IO)|diskIOReads|1.3.6.1.4.1.2021.13.15.1.1.5|UCD-DISKIO-MIB|
|Writes Accesses (Disk IO)|diskIOWrites|1.3.6.1.4.1.2021.13.15.1.1.6|UCD-DISKIO-MIB|
|Last Minute Load (Disk IO)|diskIOLA1|1.3.6.1.4.1.2021.13.15.1.1.9|UCD-DISKIO-MIB|
|Last 5 Minutes Load (Disk IO)|diskIOLA5|1.3.6.1.4.1.2021.13.15.1.1.10|UCD-DISKIO-MIB|
|Last 15 Minutes Load (Disk IO)|diskIOLA15|1.3.6.1.4.1.2021.13.15.1.1.11|UCD-DISKIO-MIB|
|Reads From (Disk IO)|diskIOReadX|1.3.6.1.4.1.2021.13.15.1.1.12|UCD-DISKIO-MIB|
|Written To (Disk IO)|diskIOWrittenX|1.3.6.1.4.1.2021.13.15.1.1.13|UCD-DISKIO-MIB|
|Index \[IDX\](If Table SNMP)|ifIndex|1.3.6.1.2.1.2.2.1.1|IF-MIB|
|Description (If Table SNMP)|ifIndex|1.3.6.1.2.1.2.2.1.2|IF-MIB|
|Type (If Table SNMP)|ifIndex|1.3.6.1.2.1.2.2.1.3|IF-MIB|
|MTU (If Table SNMP)|ifMtu|1.3.6.1.2.1.2.2.1.4|IF-MIB|
|Speed (If Table SNMP)|ifSpeed|1.3.6.1.2.1.2.2.1.5|IF-MIB|
|Physical Address (If Table SNMP)|ifPhysAddress|1.3.6.1.2.1.2.2.1.6|IF-MIB|
|Admin Status (If Table SNMP)|ifAdminStatus|1.3.6.1.2.1.2.2.1.7|IF-MIB|
|Operational Status (If Table SNMP)|ifOperStatus|1.3.6.1.2.1.2.2.1.8|IF-MIB|
|Last Change (If Table SNMP)|ifAdminStatus|1.3.6.1.2.1.2.2.1.9|IF-MIB|
|In Octets (If Table SNMP)|ifInOctets|1.3.6.1.2.1.2.2.1.10|IF-MIB|
|In Unicast Packets (If Table SNMP)|ifInOctets|1.3.6.1.2.1.2.2.1.11|IF-MIB|
|In Non Unicast Packets (If Table SNMP)|ifInUcastPkts|1.3.6.1.2.1.2.2.1.12|IF-MIB|
|In Discards (If Table SNMP)|ifInDiscards|1.3.6.1.2.1.2.2.1.13|IF-MIB|
|In Errors (If Table SNMP)|ifInErrors|1.3.6.1.2.1.2.2.1.14|IF-MIB|
|In Uknown Protocols (If Table SNMP)|ifInUnknownProtos|1.3.6.1.2.1.2.2.1.15|IF-MIB|
|Out Octets (If Table SNMP)|ifOutOctets|1.3.6.1.2.1.2.2.1.16|IF-MIB|
|Out Unicast Packets (If Table SNMP)|ifOutOctets|1.3.6.1.2.1.2.2.1.17|IF-MIB|
|Out Non Unicast Packets (If Table SNMP)|ifOutUcastPkts|1.3.6.1.2.1.2.2.1.18|IF-MIB|
|Out Discards (If Table SNMP)|ifOutDiscards|1.3.6.1.2.1.2.2.1.19|IF-MIB|
|Out Errors (If Table SNMP)|ifOutErrors|1.3.6.1.2.1.2.2.1.20|IF-MIB|
|Out Queue Length (If Table SNMP)|ifOutQLen|1.3.6.1.2.1.2.2.1.21|IF-MIB|
|Specific (If Table SNMP)|ifSpecific|1.3.6.1.2.1.2.2.1.22|IF-MIB|
|Name (IfX Table SNMP)|ifIndex|1.3.6.1.2.1.31.1.1.1.1|IF-MIB|
|In Multicast Packets (IfX Table SNMP)|ifInMulticastPkts|1.3.6.1.2.1.31.1.1.1.2|IF-MIB|
|In Broadcast Packets (IfX Table SNMP)|ifInBroadcastPkts|1.3.6.1.2.1.31.1.1.1.3|IF-MIB|
|Out Multicast Packets (IfX Table SNMP)|ifOutMulticastPkts|1.3.6.1.2.1.31.1.1.1.4|IF-MIB|
|Out Broadcast Packets (IfX Table SNMP)|ifOutBroadcastPkts|1.3.6.1.2.1.31.1.1.1.5|IF-MIB|
|High Capacity In Octets (IfX Table SNMP)|ifHCInOctets|1.3.6.1.2.1.31.1.1.1.6|IF-MIB|
|High Capacity In Unicast Packets (IfX Table SNMP)|ifHCInUcastPkts|1.3.6.1.2.1.31.1.1.1.7|IF-MIB|
|High Capacity In Multicast Packets (IfX Table SNMP)|ifHCInMulticastPkts|1.3.6.1.2.1.31.1.1.1.8|IF-MIB|
|High Capacity In Broadcast Packets (IfX Table SNMP)|ifHCInBroadcastPkts|1.3.6.1.2.1.31.1.1.1.9|IF-MIB|
|High Capacity Out Octets (IfX Table SNMP)|ifHCOutOctets|1.3.6.1.2.1.31.1.1.1.10|IF-MIB|
|High Capacity Out Unicast Packets (IfX Table SNMP)|ifHCOutUcastPkts|1.3.6.1.2.1.31.1.1.1.11|IF-MIB|
|High Capacity Out Multicast Packets (IfX Table SNMP)|ifHCOutMulticastPkts|1.3.6.1.2.1.31.1.1.1.12|IF-MIB|
|High Capacity Out Broadcast Packets (IfX Table SNMP)|ifHCOutBroadcastPkts|1.3.6.1.2.1.31.1.1.1.13|IF-MIB|
|Link Up Down Trap Enable (IfX Table SNMP)|ifLinkUpDownTrapEnable|1.3.6.1.2.1.31.1.1.1.14|IF-MIB|
|High Speed (IfX Table SNMP)|ifHighSpeed|1.3.6.1.2.1.31.1.1.1.15|IF-MIB|
|Promiscuous Mode (IfX Table SNMP)|ifPromiscuousMode|1.3.6.1.2.1.31.1.1.1.16|IF-MIB|
|Connector Present (IfX Table SNMP)|ifConnectorPresent|1.3.6.1.2.1.31.1.1.1.17|IF-MIB|
|Alias (IfX Table SNMP)|ifAlias|1.3.6.1.2.1.31.1.1.1.18|IF-MIB|
|Couter Discontinuity Time (IfX Table SNMP)|ifCouterDiscontinuityTime|1.3.6.1.2.1.31.1.1.1.19|IF-MIB|