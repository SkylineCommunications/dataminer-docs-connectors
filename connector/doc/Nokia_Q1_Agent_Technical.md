---
uid: Connector_help_Nokia_Q1_Agent_Technical
---

# Nokia Q1 Agent

This connector is a network management system that is designed to manage Nokia node devices of the **Nokia DCNA** system.

### Version Info

| Range              | Key Features     | Based on | System Impact                                                               |
|--------------------|------------------|----------|-----------------------------------------------------------------------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -                                                                           |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x |                    |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

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

The monitored devices are loaded from an XML file located on the FTP server.
The **Username**, **Password**, **FTP Sever Address**, and **File Name** parameters on the **General** page are mandatory fields that must be completed to retrieve the XML file. If the file is located in a subfolder of the root directory, please ensure that the **File Path** parameter is also filled in.

If DVEs need to be created automatically after importation, Please ensure the **DVE Auto Creation** option is enabled.

> [!IMPORTANT]
> Please note that if the **DVE Auto Creation** option is enabled, DVEs will be automatically created. This could result in a massive amount of DVEs being created.
> If you wish to know how many DVEs will be created, please use the **Check DVE Count** button to check the maximum DVEs created. The result will be displayed at the parameter **Max DVE Number Count**.

Once all the mandatory parameters are filled in, click the **Import DVE** button to import the node devices from the XML file.

## How to Use

### General

This page contains FTP configuration parameters and DVE configuration settings.

If you wish to create a DVE automatically when a node device is imported, ensure that the **Default View Name** is configured and the **DVE Auto Creation** option is enabled.

**Check DVE Count** button can be used to check the maximum possible DVEs that will be created.

### Device Management

This page is used to managing the node devices that are important from the XML file.

**Device Manegement** table  can be used to edit the device's DVE name and view. By enabling or disabling the DVE state of a device, the respective device DVE will be created or removed.

Please exercise caution when removing a DVE as once a DVE is removed, its historical alarm and trend data can no longer be accessed, even if a DVE with the same name is added back.

**Node Detailed Information** table displays the detailed information of each imported node device.

### Alarms

This page contains the **Alarms** table, which display alarms for each node device.

### Logging

This page contains the **DVE Log** table, which displays any messages that require attention during the import or creation of the node device DVE.


