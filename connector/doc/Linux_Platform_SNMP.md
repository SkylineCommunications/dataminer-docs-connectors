---
uid: Connector_help_Linux_Platform_SNMP
---

# Linux Platform SNMP

> [!IMPORTANT]
> This connector is deprecated. [Linux Platform](https://catalog.dataminer.services/details/33a5c495-60c9-4409-aecc-91f1876dacf1) should be used instead.

With this connector, you can monitor Linux platforms with SNMP.

## About

This connector uses SNMP in order to monitor a Linux platform.

### Version Info

| Range              | Description                                                                   | DCF Integration | Cassandra Compliant |
|--------------------|-------------------------------------------------------------------------------|-----------------|---------------------|
| 1.0.0.x (obsolete) | Initial version.                                                               | No | No |
| 1.1.0.x (obsolete) | Based on 1.0.0.25. <br>New firmware based on 1.0.0.x (see below). | Yes | No |
| 1.1.1.x (obsolete) | Based on 1.1.0.56. <br>Process Counter table remade. This table was created in version 1.1.0.47. <br>Impact upgrading from 1.1.0.46 or below: none. <br>Impact upgrading from 1.1.0.47 or above: **loss of trend data for Process Counter Table**. | Yes | No |
| 1.1.2.x [SLC Main] | Based on 1.1.1.8. <br>Added support for dynamic units. | Yes | No |
| 2.0.0.x | Based on 1.1.0.35. <br>Implemented SNMPv3. | Yes | No |
| 2.0.1.x | Based on 1.1.0.44. <br>Changed displayColumn to Naming to improve performance and make the connector Cassandra-compliant. <br>Impact: **loss of trend data on tables**:<br>- Software Info<br>- Storage Table<br>- Linux Monitored Disks<br>- Load Average Information<br>- Processor Table<br>- Disk IO Table<br>- Dell Power Supply Table<br>- Dell Temperature Probe Table<br>- Dell Cooling Device Table<br>- Dell Controller Table<br>- Dell Channel Table<br>- Dell Enclosure Table<br>- Dell Array Disk Table<br>- Dell Virtual Disk Table | Yes | Yes |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | Not applicable              |
| 1.1.0.x          | Not applicable              |
| 1.1.1.x          | Not applicable              |
| 1.1.2.x          | Not applicable              |
| 2.0.0.x          | Not applicable              |
| 2.0.1.x          | Not applicable              |

## Configuration

### Connections

#### SNMP main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13.*

SNMP Settings:

- **Port number**: The port of the connected device, by default *161.*
- **Get community string**: The community string in order to read from the device. The default value is *public*.
- **Set community string**: The community string in order to set to the device. The default value is *private.*

From version **2.0.0.x** onwards, depending on the **Security level and protocol** selected, you may also need to fill in the **User name**, **Authentication password** and **Encryption password**.

## Usage

### General Page

This page displays general information regarding the Linux Platform:

- **Device info**
- **Total Processor Load**: Only available if **Poll Task Manager** is enabled (on the Task Manager page).
- **Memory usage**
- etc.

The **Memory Calculation Change** parameter is used to change the calculation for the **Available Physical Memory**. Between Red Hat EL net-snmp releases 5.7.2-43 and 5.7.2-46, the memory calculation was changed to a new formula. The old formula that was used for Red Hat EL net-snmp releases prior to 5.7.2-43 is back in use since 5.7.2-47. The **default value** of the Memory Calculation Change parameter is ***Disabled***, meaning it uses the old formula. If the installed net-snmp release on the Linux server is **between 5.7.2-43 and 5.7.2-46**, **enable** this parameter to use the new formula for the memory calculation. If you notice that the current Available Physical Memory value is incorrect, toggle the Memory Calculation Change parameter value to get the correct value of the memory.

The page contains several page buttons:

- **Port**: Displays a Port List and allows you to add/remove ports manually.
- **Ping:** Allows you to configure the ping definitions.
- **Load:** Displays load information.
- **Ext Commands:** Displays a table containing extensible commands and result codes.
- **Raw CPU:** Displays detailed information on CPU usage.
- **Processor**: Displays processor load information.

### Task Manager

On this page, you can enable **Poll Task Manager** in order to retrieve all the data from the **Task Manager Table**. Click **Auto Clear Task Manager** in order to automatically clear inactive processes.

The following page buttons are available:

- **Process Counters**: Counts the number of processes running and the CPU load and Memory Usage. There are also **Export** and **Import CSV** buttons used to export/import CSV files to/from the specified path and file name. After pressing the **Export CSV** button, the user has to check the specified file name at the specified file path of the server.
- **Nominal Value**: Displays additional process information.
- **Process Validation:** Displays information regarding process validation.
- **More:** Displays the Linux Monitored Processes information.

### Network Info

This page displays all interfaces and data rates.

From version **1.1.0.53** onwards, an additional monitoring subpage is available, the **Interface Monitor Config** page:

- This page displays the **status** of all interfaces.
- In the **Monitor** column, you can enable or disable rows to configure which rows are shown in the **Interfaces Tables** on the **Network Info** page.
- Four buttons at the top of the page allow you to **Enable All** interfaces, **Disable All** interfaces, **Enable Operational Up** and **Refresh** the table.

### Memory Info

This page displays memory information in the **Storage Table**, if **Storage Table Polling** is enabled.

The following page buttons are available:

- **Storage Availability:** Displays the Storage Availability Table.
- **More Memory**: Displays additional memory information.
- **Disk IO**: Displays the Disk IO Table.

### Software Info

This page displays a list of all installed software.

### More Disks

This page displays disk info, if **Linux Monitored Disks Polling** is enabled.

One page button is available, **Mount Availability**, which shows whether the mount is available (*present/not present*).

### External Data

This page contains data that is filled in through a dynamic link to elements of type **Sun File Reader**.

### HP/Dell

If the Linux platform is installed on an HP/Dell platform, you can enable **Poll HP Parameters** or **Poll Dell Parameters** to receive specific HP or Dell data.

On the **HP General** page (from version 1.1.1.2 onwards), you can configure an alternative IP (iLo IP) from which the HP parameters have to be polled, with the **HP Polling IP** parameter. The default value for this parameter is the element IP. If you do not want to use the alternative IP, you can disable it using the **HP Polling IP Status** parameter; the connector will then reset the IP to the default element IP. In order to fill in a new IP as the **HP Polling** **IP**, make sure the **HP Polling IP Status** parameter is enabled.

The following page buttons allow access to additional HP or Dell info:

- **Fan**
- **Power Supply**
- **Temperature**
- **Memory**
- **CPU**
- **Disk**

### SuperMicro

If the Linux platform is installed on a SuperMicro platform, you can enable **Poll SuperMicro Parameters** to receive specific SuperMicro data.

The following page buttons allow access to additional SuperMicro info:

- **OS**
- **Disk**
- **Memory**
- **CPU**
- **Health**

### Huawei

If the Linux platform is installed on a Huawei platform, you can enable **Poll Huawei Parameters** to receive specific Huawei data.

The following page buttons allow access to additional Huawei info:

- **CPU**
- **Fan**
- **LDAP**
- **DNS**
- **Network**
- **Memory**
- **Storage**
- **Power Supply**
- **Temperature**
- **Components**

### Virtual Server

This page is available from version **1.1.0.41** onwards. It displays general information about the virtual server. It also allows you to enable/disable **Poll LVS Parameters** to receive the data in question.

The following page buttons allow access to additional virtual server info:

- **LVS Real Table**
- **Service Table**

## DataMiner Connectivity Framework

From version **1.1.0.29** onwards, this connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through DataMiner third-party connectors (for instance a manager).

### Interfaces

#### Dynamic Interfaces

Physical dynamic interfaces:

- The physical dynamic interface is created for the parameter **Interfaces Table** and its interface is **inout**.

## Notes

For range **1.1.0.x**, it is possible to create a virtual dynamic Interface from an external source by adding a row to the Remote DCF Interface table (49997). This functionality does not exist in the 2.0.0.x range.

## SNMP OIDs Implemented

> [!NOTE]
> The following list includes OIDs that are monitored by default when the element is created.

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
