---
uid:microsoft_platform_technical_wmi_queries
---

# Microsoft Platform - WMI Queries

In this page you will find the list of queries and properties implemented by the **Microsoft Platform** connector.

## Computer System

- Namespace: root\cimv2
- ClassName: Win32_ComputerSystem
- Documentation: [Win32_ComputerSystem class](https://learn.microsoft.com/en-us/windows/win32/cimwin32prov/win32-computersystem)

### Win32_ComputerSystem Properties

- Name
- Domain
- Model
- Manufacturer
- SystemType

## Logical Disk

- Namespace: root\cimv2
- ClassName: Win32_LogicalDisk
- Documentation: [Win32_LogicalDisk](https://learn.microsoft.com/en-us/windows/win32/cimwin32prov/win32-logicaldisk)

### Win32_LogicalDisk Properties

- DeviceId
- Name
- VolumeName
- Size
- FreeSpace
- DriveType

## Network Adapter

- Namespace: root\cimv2
- ClassName: Win32_NetworkAdapter
- Documentation: [Win32_NetworkAdapter](https://learn.microsoft.com/en-us/windows/win32/cimwin32prov/win32-networkadapter)

### Win32_NetworkAdapter Properties

- DeviceId
- Name
- Index
- MacAddress
- Manufacturer
- NetConnectionId
- NetEnabled
- NetConnectionStatus

## Network Adapter Configuration

- Namespace: root\cimv2
- ClassName: Win32_NetworkAdapterConfiguration
- Documentation: [Win32_NetworkAdapterConfiguration](https://learn.microsoft.com/en-us/windows/win32/cimwin32prov/win32-networkadapterconfiguration)

### Win32_NetworkAdapterConfiguration Properties

- Index
- IP Address

## Operating System

- Namespace: root\cimv2
- ClassName: Win32_OperatingSystes
- Documentation: [Win32_OperatingSystem class](https://learn.microsoft.com/en-us/windows/win32/cimwin32prov/win32-operatingsystem)

### Win32_OperatingSystem Properties

- Caption
- Manufacturer
- Version
- OSArchitecture
- LastBootTime
- LocalDateTime
- FreeVirtualMemory
- TotalVirtualMemorySize
- TotalVisibleMemorySize

## Perform Data Network Adapter

- Namespace: root\cimv2
- ClassName: Win32_PerfRawData_Tcpip_NetworkAdapter
- Documentation: [Win32_PerfFormattedData_Tcpip_NetworkInterface](https://learn.microsoft.com/en-us/previous-versions/aa394293(v=vs.85))

### Win32_PerfRawData_Tcpip_NetworkAdapter Properties

- Name
- BytesSentPerSec
- BytesReceivedPerSec
- BytesTotalPerSec
- FrequencyPerf_Time
- TimestampPerf_Time
- CurrentBandwidth

## Perform Data Logical Disk

- Namespace: root\cimv2
- ClassName: Win32_PerfRawData_PerfDisk_LogicalDisk
- Documentation: [Win32_PerfRawData_PerfDisk_LogicalDisk](https://wutils.com/wmi/root/cimv2/win32_perfrawdata_perfdisk_logicaldisk/)

### Win32_PerfRawData_PerfDisk_LogicalDisk Properties

- Name
- DiskReadBytesPerSec
- DiskWriteBytesPerSec
- DiskBytesPerSec
- Timestamp_Sys100NS
- PercentDiskReadTime
- PercentDiskWriteTime
- PercentDiskTime
- AvgDiskSecPerRead
- AvgDiskSecPerWrite
- AvgDiskSecPerTransfer
- AvgDiskSecPerRead_Base
- AvgDiskSecPerWrite_Base
- AvgDiskSecPerTransfer_Base
- Frequency_PerfTime

## Perform Data OS Memory

- Namespace: root\cimv2
- ClassName: Win32_PerfRawData_PerfOS_Memory
- Documentation: [Win32_PerfRawData_PerfOS_Memory](https://wutils.com/wmi/root/cimv2/win32_perfrawdata_perfos_memory/)

### Win32_PerfRawData_PerfOS_Memory Properties

- AvailableBytes
- CommitLimit
- CommittedBytes
- PoolNonPagedBytes
- PoolPagedBytes

## Perform Data OS Processor

- Namespace: root\cimv2
- ClassName: Win32_PerfRawData_PerfOS_Processor
- Documentation:[Win32_PerfRawData_PerfOS_Processor](https://wutils.com/wmi/root/cimv2/win32_perfrawdata_perfos_processor/)

### Win32_PerfRawData+PerfOS_Processor Properties

- Name
- PercentProcessorTime
- Timestamp_Sys100NS

## Perform Data OS System

- Namespace: root\cimv2
- ClassName: Win32_PerfRawData_PerfOS_System
- Documentation: [Win32_PerfRawData_PerfOS_System](https://wutils.com/wmi/root/cimv2/win32_perfrawdata_perfos_system/)

### Win32_PerfRawData_PerfOS_System Properties

- Threads
- Processes
- ProcessorQueueLength

## Perform Data Process

- Namespace: root\cimv2
- ClassName: Win32_PerfRawData_PerfProc_Process
- Documentation: [Win32_PerfRawData_PerfProc_Process](https://learn.microsoft.com/en-us/previous-versions/aa394323(v=vs.85))

### Win32_PerfRawData_PerfProc_Process Properties

- HandleCount
- PercentProcessorTime
- Timestamp_Sys100NS
- IDProcess
- ThreadCount
- IODataBytesPerSec
- IOOtherBytesPerSec
- IOReadBytesPerSec
- IOWriteBytesPerSec
- WorkingSetPrivate

## Processes

- Namespace: root\cimv2
- ClassName: Win32_Process
- Documentation [Win32_Process](https://learn.microsoft.com/en-us/windows/win32/cimwin32prov/win32-process)

### Win32_Process Properties

- CommandLine
- CreationDate
- Name
- ProcessId
- PageFileUsage
- VirtualSize
- WorkingSetSize

## Processor

- Namespace: root\cimv2
- ClassName: Win32_Processor
- Documentation [Win32_Processor](https://learn.microsoft.com/en-us/windows/win32/cimwin32prov/win32-processor)

### Win32_Processor

- Name
- NumberOfCores
- NumberOfLogicalProcessors

## Product

- Namespace: root\cimv2
- ClassName: Win32_Product
- Documentation [Win32_Product](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/legacy/aa394378(v=vs.85))

### Win32_Product Properties

- IdentifyingNumber
- Name
- Vendor
- Version
- InstallDate
- InstallState

## QuickFix Engineering (Patches)

- Namespace: root\cimv2
- ClassName: Win32_QuickFixEngineering
- Documentation [Win32_QuickFixEngineering](https://learn.microsoft.com/en-us/windows/win32/cimwin32prov/win32-quickfixengineering)

### Win32_QuickFixEngineering Properties

- HotFixID
- Description
- InstalledOn

## Services

- Namespace: root\cimv2
- ClassName: Win32_Service
- Documentation [Win32_Service](https://learn.microsoft.com/en-us/windows/win32/cimwin32prov/win32-service)

### Win32_Service Properties

- Name
- DisplayName
- ProcessId
- State
- Status
- StartMode
- Description
