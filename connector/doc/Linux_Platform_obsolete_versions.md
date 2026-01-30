---
uid: Connector_help_Linux_Platform_obsolete_versions
---

# Linux Platform (Obsolete Versions)

## About

With this connector, you can monitor servers running Linux OS with SSH or with SNMP.

>[!IMPORTANT]
> This documentation covers obsolete versions of the Linux Platform connector (**1.0.0.x - 1.1.1.x**). For the latest version, refer to [Linux Platform](xref:Connector_help_Linux_Platform).

### Supported Distributions

- Debian-based distributions (for example, Ubuntu, Linux Mint)
- Red Hat-based distributions (for example, CentOS, Fedora)

> [!IMPORTANT]
> Distributions based on BusyBox (for example, Alpine Linux) are currently not supported for SSH. However, it is possible to monitor via SNMP if the SNMP agent is properly configured.

## Configuration

### Serial connection

- **IP address/host:** The polling IP of the Linux platform.
- **IP port:** The IP port of the device.

## Usage

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

### HP/Dell (1.1.1.x only)

From version **1.1.1.x** onwards, in case this connector is monitoring a Linux host running on a physical server, you can enable the HP/Dell monitoring options (depending on the server brand) to get additional information (see parameters **Poll HP Parameters** and **Poll Dell Parameters**).

>[!IMPORTANT]
> In case you plan to monitor HP/Dell metrics, the SNMP connection of the element must be configured with the IP address assigned to the management interface of the physical server (iLO for HP and iDRAC for Dell).

## DataMiner Connectivity Framework

From version **1.1.0.7** onwards, this connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (for instance a manager).

### Interfaces

#### Dynamic Interfaces

Physical dynamic interfaces:

- The physical dynamic interface is created for the parameter **Network Interface Table** and its interface is **inout**.

## Notes

For additional technical information, refer to [Linux Platform - SNMP Mapping](xref:Connector_help_Linux_Platform_snmp_Mapping) and [Memory Calculation](xref:Connector_help_Linux_Platform_Memory_Calculation).
