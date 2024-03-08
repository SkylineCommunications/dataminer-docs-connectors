---
uid: Connector_help_Nokia_NSP
---

# Nokia NSP

This connector is used to collect alarm data from the **Nokia NSP** system, which is a network management system that is designed to manage Nokia proprietary devices.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 23.11              |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTPS connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. This should always start with `https://`.
- **IP port**: Default: *8443*.

##### Initialization

In order to perform requests, you first need to configure the **User Name** and **Password** parameters on the General page.

## How to use

The connector contains the following data pages:

- **General**: Contains the **User Name** and **Password** parameters. If these parameters are not defined, the connector cannot request any data.

- **Alarms**: Contains the **Alarms Filtering Path** parameter, which allows you to to define a path to an .xml file containing a fault filter. This .xml file is used to retrieve only some filtered alarms defined by the user. It must have the structure detailed in section **11.6.2** of the **Nokia NSP XML API Developer Guide**. If no path is defined to the .xml file, or if the file does not have the correct structure, the connector will retrieve all alarms present in the system. The retrieved information is displayed in the **Alarms** table.

- **Probable Cause Configuration/Alarm Name Configuration/Alarm Type Configuration**: By default, for the columns **Probable Cause/Alarm Name/Alarm Type** in the Alarms table, what is retrieved from the device are the IDs of the respective columns. On these configuration pages, you can define descriptions for these IDs, to be shown in the Alarms table for these columns.

  For example, on the **Probable Cause Configuration** page, to **add** a new entry to the **Alarm Probable Cause** table, first fill in the **Alarm Probable Cause ID** and **Alarm Probable Cause Description** parameters (both of these parameters need to be unique), then click **Add entry**. You can also **edit** an existing description in the **Description** column, and you can **remove** an entry with the **Delete Entry** button in the table.

- **Polling Configuration**: On this page, you can select which of the available requests is polled and when. You can also poll the requests on demand with the **Poll** button for each entry in the table.
