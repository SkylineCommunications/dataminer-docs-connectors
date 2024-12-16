---
uid: Connector_help_Microsoft_Platform_SNMP
---

# Microsoft Platform SNMP

With the **Microsoft Platform** connector, it is possible to monitor a Microsoft server.

## About

The Microsoft Platform connector retrieves basic information from a Microsoft server. Extra information can be enabled or disabled, e.g. Task Manager, Service List, etc.
On the Task Manager page, a button allows you to normalize alarms in order to set the current values as normal.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|----------------------|-----------------|---------------------|-------------------------|
| 1.1.0.x [SLC Main]   | Initial version | Yes                 | Yes                     |

### Product Info

| Range     | Device Firmware Version                                             |
|------------------|---------------------------------------------------------------------|
| 1.1.0.x          | All Windows and Windows Server versions with built-in SNMP service. |

## Installation and configuration

### Creation

#### SNMP Main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public.*
- **Set community string**: The community string used when setting values on the device, by default *private*.

## Usage

### General

This page displays general system information.

### Task Manager

On this page, a list of all the running processes is displayed in a table.

To clear all processes that are no longer running from the table, click the button **Clear Task Manager** at the top of the page. You can also enable automatic removal of processes that are not running by setting the parameter **Auto Clear Task Manager** to **On**.

To set the current values in the table as the normal reference for alarms, click the button **Normalize Alarms**. You can then view these references via the **Nominal** **Values** button at the bottom of the page.

In the right-click menu of the Task Manager table, you can select **Validate Processes** to add the selected process or processes to the Processes Validation table.

### Process Validation

This page allows you to validate selected processes according to features such as the number of active process instances in order to monitor inactive processes.

The following options are available in the right-click menu of the **Processes Validation** table:

- **Remove Processes**: Removes the selected process or processes from Processes Validation table.
- **Add Process**: Allows you to add a process with the provided process name to the Processes Validation table. You can use this to add inactive processes.

### Services

This page shows all active services that are being monitored from the **Service Monitor Config** page.

To enable or disable the polling of the service list, click the toggle button next to **Poll Services**.

When polling is enabled, active services with their status, description, etc. will be shown in the table on the **Service Monitor Config** page.

The following options are available in the right-click menu of the Services table:

- **Validate Services**: Add the selected service(s) to the Services Validation table.

### Service Monitor Config

This page allows you to monitor individual active services. Monitored services will be listed in the Services table.

### Service Validation

This page allows you to validate selected services according to features such as availability in order to monitor inactive services.

The following options are available in the right-click menu of the Services Validation table:

- **Remove Services**: Removes the selected service(s) from Services Validation table.

- **Add Service**: Allows you to add a service with the provided service name to the Services Validation table. You can use this to add inactive services.

### Network Info

This page displays a table with the different network adapters on the server. For each adapter, additional information is shown, such as the **Utilization**, **Tx Speed**, **Rx Speed**, etc.

The **Interface Monitor Config** page allows you to *enable* or *disable* the polling of individual interfaces. It also contains the **Enable Operational Up** button, which reads the status of the table and adjusts the value of the **IF Monitor** row accordingly.

### Disk Info

This page displays a table with all the disk information, such as the **Capacity**, **Used Space**, **Free Space**, etc.

### Software Info

This page displays a table with all the **installed software** and the **installation date**.

### HP

These pages display HP-specific information, such as **Temperature**, **Power Supply**, **Fan**, **Disk**, **CPU** and **Memory**.

### DELL

These pages display DELL-specific information, such as **Temperature**, **Power Supply**, **Fan**, **Disk**, **CPU** and **Memory**.

### SuperMicro

If the Microsoft platform is installed on a SuperMicro platform, you can enable **Poll SuperMicro Parameters** to receive specific SuperMicro data.

The following page buttons allow access to additional SuperMicro info:

- **OS:** Displays the SuperMicro Operating System Table.
- **Disk:** Displays the SuperMicro Disk Table.
- **Memory:** Displays the SuperMicro Memory Table.
- **CPU:** Displays the SuperMicro CPU Table.
- **Health Monitor:** Displays the SuperMicro Health Monitor Table.

### Huawei

If the Microsoft platform is installed on a Huawei platform, you can enable **Poll Huawei Parameters** to receive specific Huawei data.

Note: To poll Huawei parameters, you must **configure the specific IP address** for this action (IP address : Port).

The following page buttons allow access to additional Huawei info:

- **CPU:** Displays the Huawei **CPU Health Status** and the **CPU Table**.
- **Fan:** Displays the Huawei **Fan Health Status**, **Level**, **Mode** and the **Fan Table**.
- **LDAP:** Displays the **LDAP Status** toggle button and parameters and tables for LDAP 1, LDAP 2 and LDAP 3.
- **DNS:** Displays standalone parameters to read/modify DNS parameters.
- **Network:** Displays the Huawei Network Table.
- **Memory:** Displays the Huawei **Memory Health Status** and the **Memory Table**.
- **Storage:** Displays the Huawei **Storage Health Status** and the **Storage Table**.
- **Power Supply:** Displays Huawei **Power Supply** standalone parameters and the **Power Supply Table**.
- **Temperature:** Displays the Huawei Temperature Table.
- **Components:** Displays the Huawei Component Table.

## DataMiner Connectivity Framework

DCF is supported from version 1.1.0.11 of the connector onwards and requires DataMiner version 8.5.3 or higher.

DCF can also be implemented through the DataMiner DCF user interface and through DataMiner third-party connectors (for instance a manager).

### Interfaces

#### Dynamic Interfaces

Physical dynamic interfaces:

- A DCF interface is created for each **monitored network interface**. The interface type is inout.

## Notes

To be able to poll using SNMP, the client Microsoft machine needs the SNMP service to be configured correctly (community strings and accepted hosts).

In order to correctly configure the SNMP service on devices running a Windows Server OS, make sure the following features are enabled:

- SNMP Service
- Remote Server Administration Tools -> Feature Administration Tools -> SNMP Tools. This feature allows additional settings in the SNMP agent (e.g. setting the community string, defining hosts that can monitor the server, etc.)

For more information on how to enable features on Windows Server, refer to [Microsoft Learn](https://learn.microsoft.com/en-us/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#install-roles-role-services-and-features-by-using-the-add-roles-and-features-wizard).
