---
uid: Connector_help_Linux_Platform_snmp_Mapping
---

# Linux Platform - SNMP Mapping

The table below lists the SNMP OIDs mapped into the Linux Platform connector.

The list includes OIDs that are monitored by default when the element is created.

| Parameter Name                                       | SNMP Parameter Name (MIB File) | SNMP OID                      | MIB File           |
|------------------------------------------------------|--------------------------------|-------------------------------|--------------------|
| System Description                                   | sysDescr                       | 1.3.6.1.2.1.1.1.0             | RFC1213-MIB        |
| System Uptime                                        | sysUpTime                      | 1.3.6.1.2.1.1.3.0             | RFC1213-MIB        |
| System Name                                          | sysName                        | 1.3.6.1.2.1.1.6.0             | RFC1213-MIB        |
| System Location                                      | sysLocation                    | 1.3.6.1.2.1.1.6.0             | RFC1213-MIB        |
| HR System Uptime                                     | hrSystemUptime                 | 1.3.6.1.2.1.25.1.1.0          | HOST-RESOURCES-MIB |
| SNMP Engine Time                                     | snmpEngineTime                 | 1.3.6.1.6.3.10.2.1.3.0        | SNMP-FRAMEWORK-MIB |
| Total Processor Load                                 | IaLoad                         | 1.3.6.1.4.1.2021.10.1.3.1     | UCD-SNMP-MIB       |
| Available Physical Memory                            | memTotalFree                   | 1.3.6.1.4.1.2021.4.11.0       | UCD-SNMP-MIB       |
| Total Real Memory                                    | memTotReal                     | 1.3.6.1.4.1.2021.4.5.0        | UCD-SNMP-MIB       |
| Number of Users                                      | hrSystemNumUsers               | 1.3.6.1.2.1.25.1.5.0          | HOST-RESOURCES-MIB |
| Number of Processes                                  | hrSystemProcesses              | 1.3.6.1.2.1.25.1.6.0          | HOST-RESOURCES-MIB |
| Total Swap Memory                                    | memTotalSwap                   | 1.3.6.1.4.1.2021.4.3.0        | UCD-SNMP-MIB       |
| Available Swap Memory                                | memAvailSwap                   | 1.3.6.1.4.1.2021.4.4.0        | UCD-SNMP-MIB       |
| Available Real Memory                                | memAvailReal                   | 1.3.6.1.4.1.2021.4.6.0        | UCD-SNMP-MIB       |
| Memory Buffer                                        | memBuffer                      | 1.3.6.1.4.1.2021.4.14.0       | UCD-SNMP-MIB       |
| Memory Cached                                        | memCached                      | 1.3.6.1.4.1.2021.4.15.0       | UCD-SNMP-MIB       |
| System CPU                                           | cpuSystemPercentage            | 1.3.6.1.4.1.2021.11.10.0      | UCD-SNMP-MIB       |
| Local Time SNMP                                      | hrSystemDate                   | 1.3.6.1.2.1.25.1.2.0          | HOST-RESOURCES-MIB |
| Raw CPU User                                         | ssCpuRawUser                   | 1.3.6.1.4.1.2021.11.50.0      | UCD-SNMP-MIB       |
| Raw CPU Nice                                         | ssCpuRawNice                   | 1.3.6.1.4.1.2021.11.51.0      | UCD-SNMP-MIB       |
| Raw CPU System                                       | ssCpuRawSystem                 | 1.3.6.1.4.1.2021.11.52.0      | UCD-SNMP-MIB       |
| Raw CPU Idle                                         | ssCpuRawIdle                   | 1.3.6.1.4.1.2021.11.53.0      | UCD-SNMP-MIB       |
| Raw CPU Wait                                         | ssCpuRawWait                   | 1.3.6.1.4.1.2021.11.54.0      | UCD-SNMP-MIB       |
| Raw CPU Kernel                                       | ssCpuRawKernel                 | 1.3.6.1.4.1.2021.11.55.0      | UCD-SNMP-MIB       |
| Raw CPU Interrupt                                    | ssCpuRawInterrupt              | 1.3.6.1.4.1.2021.11.56.0      | UCD-SNMP-MIB       |
| PID (Task Manager)                                   | hrSWRunIndex                   | 1.3.6.1.2.1.25.4.2.1.1        | HOST-RESOURCES-MIB |
| Name (Task Manager)                                  | hrSWRunName                    | 1.3.6.1.2.1.25.4.2.1.2        | HOST-RESOURCES-MIB |
| CPU Time (Task Manager)                              | hrSWRunPerfCPU                 | 1.3.6.1.2.1.25.5.1.1.1        | HOST-RESOURCES-MIB |
| Memory Usage (Task Manager)                          | hrSWRunPerfMem                 | 1.3.6.1.2.1.25.5.1.1.2        | HOST-RESOURCES-MIB |
| Status (Task Manager)                                | hrSystemMaxProcesses           | 1.3.6.1.2.1.25.4.2.1.7        | HOST-RESOURCES-MIB |
| Full Path (Task Manager)                             | hrSWRunPath                    | 1.3.6.1.2.1.25.4.2.1.4        | HOST-RESOURCES-MIB |
| Run Parameters (Task Manager)                        | hrSWRunParameters              | 1.3.6.1.2.1.25.4.2.1.5        | HOST-RESOURCES-MIB |
| Firmware (Processor)                                 | hrProcessorFrwID               | 1.3.6.1.2.1.25.3.3.1.1        | HOST-RESOURCES-MIB |
| Load (Processor)                                     | hrProcessorLoad                | 1.3.6.1.2.1.25.3.3.1.2        | HOST-RESOURCES-MIB |
| Device Type (Devices)                                | hrDeviceType                   | 1.3.6.1.2.1.25.3.2.1.2        | HOST-RESOURCES-MIB |
| Device Description (Devices)                         | hrDeviceDescr                  | 1.3.6.1.2.1.25.3.2.1.3        | HOST-RESOURCES-MIB |
| Device ID (Devices)                                  | hrDeviceID                     | 1.3.6.1.2.1.25.3.2.1.4        | HOST-RESOURCES-MIB |
| Device Status (Devices)                              | hrDeviceStatus                 | 1.3.6.1.2.1.25.3.2.1.5        | HOST-RESOURCES-MIB |
| Device Errors (Devices)                              | hrDeviceErrors                 | 1.3.6.1.2.1.25.3.2.1.6        | HOST-RESOURCES-MIB |
| Index (Load Average Information)                     | IaIndex                        | 1.3.6.1.4.1.2021.10.1.1       | UCD-SNMP-MIB       |
| Description \[IDX\] (Load Average Information)       | IaNames                        | 1.3.6.1.4.1.2021.10.1.1       | UCD-SNMP-MIB       |
| Load (Load Average Information)                      | IaLoad                         | 1.3.6.1.4.1.2021.10.1.3       | UCD-SNMP-MIB       |
| Name \[IDX\](Software Installed)                     | hrSWInstalledName              | 1.3.6.1.2.1.25.6.3.1.2        | HOST-RESOURCES-MIB |
| ID (Software Installed)                              | hrSWInstalledID                | 1.3.6.1.2.1.25.6.3.1.3        | HOST-RESOURCES-MIB |
| Type (Software Installed)                            | hrSWInstalledType              | 1.3.6.1.2.1.25.6.3.1.4        | HOST-RESOURCES-MIB |
| Index (Disks)                                        | dskIndex                       | 1.3.6.1.4.1.2021.9.1.1        | UCD-SNMP-MIB       |
| Path \[IDX\] (Disks)                                 | dskPath                        | 1.3.6.1.4.1.2021.9.1.2        | UCD-SNMP-MIB       |
| Device (Disks)                                       | dskDevice                      | 1.3.6.1.4.1.2021.9.1.3        | UCD-SNMP-MIB       |
| Total Minimum Space (Disks)                          | dskMinimum                     | 1.3.6.1.4.1.2021.9.1.4        | UCD-SNMP-MIB       |
| Minimum Space (Disks)                                | dskMinPercentage               | 1.3.6.1.4.1.2021.9.1.5        | UCD-SNMP-MIB       |
| Total Size (Disks)                                   | dskTotal                       | 1.3.6.1.4.1.2021.9.1.6        | UCD-SNMP-MIB       |
| Available Space (Disks)                              | dskAvail                       | 1.3.6.1.4.1.2021.9.1.7        | UCD-SNMP-MIB       |
| Total Memory Used (Disks)                            | dskUsed                        | 1.3.6.1.4.1.2021.9.1.8        | UCD-SNMP-MIB       |
| Memory Used (Disks)                                  | dskPercent                     | 1.3.6.1.4.1.2021.9.1.9        | UCD-SNMP-MIB       |
| Inodes Used (Disks)                                  | dskPercentNode                 | 1.3.6.1.4.1.2021.9.1.10       | UCD-SNMP-MIB       |
| Total Size Low (Disks)                               | dskTotalLow                    | 1.3.6.1.4.1.2021.9.1.11       | UCD-SNMP-MIB       |
| Total Size High (Disks)                              | dskTotalHigh                   | 1.3.6.1.4.1.2021.9.1.12       | UCD-SNMP-MIB       |
| Available Space Low (Disks)                          | dskAvailLow                    | 1.3.6.1.4.1.2021.9.1.13       | UCD-SNMP-MIB       |
| Available Space High (Disks)                         | dskAvailHigh                   | 1.3.6.1.4.1.2021.9.1.14       | UCD-SNMP-MIB       |
| Total Memory Used Low (Disks)                        | dskUsedLow                     | 1.3.6.1.4.1.2021.9.1.15       | UCD-SNMP-MIB       |
| Total Memory Used High (Disks)                       | dskUsedHigh                    | 1.3.6.1.4.1.2021.9.1.16       | UCD-SNMP-MIB       |
| Index (Disk IO)                                      | diskIOIndex                    | 1.3.6.1.4.1.2021.13.15.1.1.1  | UCD-DISKIO-MIB     |
| Device (Disk IO)                                     | diskIODevice                   | 1.3.6.1.4.1.2021.13.15.1.1.2  | UCD-DISKIO-MIB     |
| Read (Disk IO)                                       | diskIONRead                    | 1.3.6.1.4.1.2021.13.15.1.1.3  | UCD-DISKIO-MIB     |
| Written (Disk IO)                                    | diskIONWritten                 | 1.3.6.1.4.1.2021.13.15.1.1.4  | UCD-DISKIO-MIB     |
| Reads Accesses (Disk IO)                             | diskIOReads                    | 1.3.6.1.4.1.2021.13.15.1.1.5  | UCD-DISKIO-MIB     |
| Writes Accesses (Disk IO)                            | diskIOWrites                   | 1.3.6.1.4.1.2021.13.15.1.1.6  | UCD-DISKIO-MIB     |
| Last Minute Load (Disk IO)                           | diskIOLA1                      | 1.3.6.1.4.1.2021.13.15.1.1.9  | UCD-DISKIO-MIB     |
| Last 5 Minutes Load (Disk IO)                        | diskIOLA5                      | 1.3.6.1.4.1.2021.13.15.1.1.10 | UCD-DISKIO-MIB     |
| Last 15 Minutes Load (Disk IO)                       | diskIOLA15                     | 1.3.6.1.4.1.2021.13.15.1.1.11 | UCD-DISKIO-MIB     |
| Reads From (Disk IO)                                 | diskIOReadX                    | 1.3.6.1.4.1.2021.13.15.1.1.12 | UCD-DISKIO-MIB     |
| Written To (Disk IO)                                 | diskIOWrittenX                 | 1.3.6.1.4.1.2021.13.15.1.1.13 | UCD-DISKIO-MIB     |
| Index \[IDX\](If Table SNMP)                         | ifIndex                        | 1.3.6.1.2.1.2.2.1.1           | IF-MIB             |
| Description (If Table SNMP)                          | ifIndex                        | 1.3.6.1.2.1.2.2.1.2           | IF-MIB             |
| Type (If Table SNMP)                                 | ifIndex                        | 1.3.6.1.2.1.2.2.1.3           | IF-MIB             |
| MTU (If Table SNMP)                                  | ifMtu                          | 1.3.6.1.2.1.2.2.1.4           | IF-MIB             |
| Speed (If Table SNMP)                                | ifSpeed                        | 1.3.6.1.2.1.2.2.1.5           | IF-MIB             |
| Physical Address (If Table SNMP)                     | ifPhysAddress                  | 1.3.6.1.2.1.2.2.1.6           | IF-MIB             |
| Admin Status (If Table SNMP)                         | ifAdminStatus                  | 1.3.6.1.2.1.2.2.1.7           | IF-MIB             |
| Operational Status (If Table SNMP)                   | ifOperStatus                   | 1.3.6.1.2.1.2.2.1.8           | IF-MIB             |
| Last Change (If Table SNMP)                          | ifAdminStatus                  | 1.3.6.1.2.1.2.2.1.9           | IF-MIB             |
| In Octets (If Table SNMP)                            | ifInOctets                     | 1.3.6.1.2.1.2.2.1.10          | IF-MIB             |
| In Unicast Packets (If Table SNMP)                   | ifInOctets                     | 1.3.6.1.2.1.2.2.1.11          | IF-MIB             |
| In Non Unicast Packets (If Table SNMP)               | ifInUcastPkts                  | 1.3.6.1.2.1.2.2.1.12          | IF-MIB             |
| In Discards (If Table SNMP)                          | ifInDiscards                   | 1.3.6.1.2.1.2.2.1.13          | IF-MIB             |
| In Errors (If Table SNMP)                            | ifInErrors                     | 1.3.6.1.2.1.2.2.1.14          | IF-MIB             |
| In Uknown Protocols (If Table SNMP)                  | ifInUnknownProtos              | 1.3.6.1.2.1.2.2.1.15          | IF-MIB             |
| Out Octets (If Table SNMP)                           | ifOutOctets                    | 1.3.6.1.2.1.2.2.1.16          | IF-MIB             |
| Out Unicast Packets (If Table SNMP)                  | ifOutOctets                    | 1.3.6.1.2.1.2.2.1.17          | IF-MIB             |
| Out Non Unicast Packets (If Table SNMP)              | ifOutUcastPkts                 | 1.3.6.1.2.1.2.2.1.18          | IF-MIB             |
| Out Discards (If Table SNMP)                         | ifOutDiscards                  | 1.3.6.1.2.1.2.2.1.19          | IF-MIB             |
| Out Errors (If Table SNMP)                           | ifOutErrors                    | 1.3.6.1.2.1.2.2.1.20          | IF-MIB             |
| Out Queue Length (If Table SNMP)                     | ifOutQLen                      | 1.3.6.1.2.1.2.2.1.21          | IF-MIB             |
| Specific (If Table SNMP)                             | ifSpecific                     | 1.3.6.1.2.1.2.2.1.22          | IF-MIB             |
| Name (IfX Table SNMP)                                | ifIndex                        | 1.3.6.1.2.1.31.1.1.1.1        | IF-MIB             |
| In Multicast Packets (IfX Table SNMP)                | ifInMulticastPkts              | 1.3.6.1.2.1.31.1.1.1.2        | IF-MIB             |
| In Broadcast Packets (IfX Table SNMP)                | ifInBroadcastPkts              | 1.3.6.1.2.1.31.1.1.1.3        | IF-MIB             |
| Out Multicast Packets (IfX Table SNMP)               | ifOutMulticastPkts             | 1.3.6.1.2.1.31.1.1.1.4        | IF-MIB             |
| Out Broadcast Packets (IfX Table SNMP)               | ifOutBroadcastPkts             | 1.3.6.1.2.1.31.1.1.1.5        | IF-MIB             |
| High Capacity In Octets (IfX Table SNMP)             | ifHCInOctets                   | 1.3.6.1.2.1.31.1.1.1.6        | IF-MIB             |
| High Capacity In Unicast Packets (IfX Table SNMP)    | ifHCInUcastPkts                | 1.3.6.1.2.1.31.1.1.1.7        | IF-MIB             |
| High Capacity In Multicast Packets (IfX Table SNMP)  | ifHCInMulticastPkts            | 1.3.6.1.2.1.31.1.1.1.8        | IF-MIB             |
| High Capacity In Broadcast Packets (IfX Table SNMP)  | ifHCInBroadcastPkts            | 1.3.6.1.2.1.31.1.1.1.9        | IF-MIB             |
| High Capacity Out Octets (IfX Table SNMP)            | ifHCOutOctets                  | 1.3.6.1.2.1.31.1.1.1.10       | IF-MIB             |
| High Capacity Out Unicast Packets (IfX Table SNMP)   | ifHCOutUcastPkts               | 1.3.6.1.2.1.31.1.1.1.11       | IF-MIB             |
| High Capacity Out Multicast Packets (IfX Table SNMP) | ifHCOutMulticastPkts           | 1.3.6.1.2.1.31.1.1.1.12       | IF-MIB             |
| High Capacity Out Broadcast Packets (IfX Table SNMP) | ifHCOutBroadcastPkts           | 1.3.6.1.2.1.31.1.1.1.13       | IF-MIB             |
| Link Up Down Trap Enable (IfX Table SNMP)            | ifLinkUpDownTrapEnable         | 1.3.6.1.2.1.31.1.1.1.14       | IF-MIB             |
| High Speed (IfX Table SNMP)                          | ifHighSpeed                    | 1.3.6.1.2.1.31.1.1.1.15       | IF-MIB             |
| Promiscuous Mode (IfX Table SNMP)                    | ifPromiscuousMode              | 1.3.6.1.2.1.31.1.1.1.16       | IF-MIB             |
| Connector Present (IfX Table SNMP)                   | ifConnectorPresent             | 1.3.6.1.2.1.31.1.1.1.17       | IF-MIB             |
| Alias (IfX Table SNMP)                               | ifAlias                        | 1.3.6.1.2.1.31.1.1.1.18       | IF-MIB             |
| Counter Discontinuity Time (IfX Table SNMP)          | ifCouterDiscontinuityTime      | 1.3.6.1.2.1.31.1.1.1.19       | IF-MIB             |
