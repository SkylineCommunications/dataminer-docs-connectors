---
uid: Connector_help_Nokia_Q1_Agent_Technical
---

# Nokia Q1 Agent

## About

This connector is a network management system that is designed to manage Nokia node devices of the **Nokia DCNA** system.

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Initialization

The monitored devices are **loaded from an XML file** located on the FTP server.

To make sure the connector can retrieve this file, go to the **General** page and specify the **Username**, **Password**, **FTP Server Address**, and **File Name**. If the file is located in a subfolder of the root directory, make sure that the **File Path** parameter is also filled in.

If DVEs need to be created automatically after the import, make sure the **DVE Auto Creation** option is enabled.

> [!IMPORTANT]
> If the **DVE Auto Creation** option is enabled, DVEs will be created automatically. This could result in a massive number of DVEs being created. If you wish to know how many DVEs will be created, use the **Check DVE Count** button to check the maximum number of DVEs that will be created. The result will be displayed by the parameter **Max DVE Number Count**.

Once all the mandatory parameters are filled in, click the **Import DVE** button to import the node devices from the XML file.

## How to Use

### General

This page contains FTP configuration parameters and DVE configuration settings.

If you wish to create a DVE automatically when a node device is imported, make sure that the **Default View Name** is configured and the **DVE Auto Creation** option is enabled.

With the **Check DVE Count** button, you can check the maximum possible number of DVEs that will be created.

### Device Management

This page is used to manage the node devices that are imported from the XML file.

In the **Device Management** table, you can edit the DVE name and view for the node devices. When the DVE state of a device is enabled or disabled, the corresponding device DVE will be created or removed, respectively.

> [!IMPORTANT]
> Exercise caution when removing a DVE. Once a DVE has been removed, its historical alarm and trend data can no longer be accessed, even if a DVE with the same name is added again.

The **Node Detailed Information** table displays the detailed information of each imported node device.

### Alarms

This page contains the **Alarms** table, which display alarms for each node device.

### Logging

This page contains the **DVE Log** table, which displays any messages that require attention during the import or creation of node device DVEs.
