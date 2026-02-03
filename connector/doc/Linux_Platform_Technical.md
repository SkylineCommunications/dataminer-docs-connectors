---
uid: Connector_help_Linux_Platform_Technical
---

# Linux Platform

## About

With this connector, you can monitor servers running Linux OS with SSH or with SNMP.

### Supported Distributions

- Debian-based distributions (for example, Ubuntu, Linux Mint)
- Red Hat-based distributions (for example, CentOS, Fedora)

> [!IMPORTANT]
> Distributions based on BusyBox (for example, Alpine Linux) are currently not supported for SSH. However, it is possible to monitor via SNMP if the SNMP agent is properly configured.

## Configuration

### SNMP Connection

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13.*
- **Port number:** The port of the connected device, by default 161.
- **Get community string:** The community string in order to read from the device, by default *public*.
- **Set community string:** The community string in order to set to the device, by default *private*.

### Serial Connection

- **IP address/host:** The polling IP of the Linux platform.
- **IP port:** The IP port of the device, by default *22* (SSH).

### Configuration SSH

In the **General page**, click **Configuration** to set up the **SSH configuration** and to select the connection type, **SNMP** or **SSH**.

## Usage

### General

This page displays general information regarding the Linux platform, such as **Device info**, **Total Processor Load**, **Memory usage**, etc.

The page contains several page buttons:

- **Ping**: Allows you to configure the ping definitions.
- **Load**: Displays load information.
- **Raw CPU**: Displays detailed information on CPU usage.
- **Processor**: Displays processor load information.
- **Configuration**: Allows you to specify the SSH username and password and to choose the connection type.

> [!IMPORTANT]
> When in SSH Mode, the Processor table will use different indexes for each processor, as there is no way to match the indexes with SNMP. This means **switching between SSH and SNMP will lead to loss of alarm and trend data**.

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

In case the connector is set to poll the Linux host using SNMP protocol, the **Disks IO** and **Disk** tables will only show data if the configuration setting of the SNMP agent allows it. Please refer to the documentation of the SNMP agent (snmpd.conf man page) for more information on how to enable this setting. For example, in Net-SNMP, it is required to add the following setting to the snmpd.conf file:

```text
includeAllDisks MINPERCENT%
```

This setting will configure monitoring of all disks using the specified (percentage) threshold.

### Software Info

This page displays the **Software Installed** table, which lists the software installed on the server.

### HP/Dell

In case this connector is monitoring a Linux host running on a physical server, you can enable the HP/Dell monitoring options (depending on the server brand) to get additional information (see parameters **Poll HP Parameters** and **Poll Dell Parameters**).

> [!IMPORTANT]
> In case you plan to monitor HP/Dell metrics, the SNMP connection of the element must be configured with the IP address assigned to the management interface of the physical server (iLO for HP and iDRAC for Dell).

### Virtual Server

This page displays general information about the virtual server. It also allows you to enable/disable **Poll LVS Parameters** to receive the data in question.

The following page buttons allow access to additional virtual server info:

- **LVS Real Table**
- **Service Table**

## DataMiner Connectivity Framework (DCF)

Currently, this main connector range does not support the DataMiner Connectivity Framework (DCF).

## Notes

For additional technical information, refer to [Linux Platform - SNMP Mapping](xref:Connector_help_Linux_Platform_snmp_Mapping) and [Memory Calculation](xref:Connector_help_Linux_Platform_Memory_Calculation).
