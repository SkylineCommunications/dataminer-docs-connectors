---
uid: Connector_help_Nokia_NSP
---

# Nokia NSP

This connector is used to collect alarms data from the **Nokia NSP** system, that is a network management system that is designed to manage Nokia proprietary devices.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 23.11               |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTPS connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination. Should always start with `https://`
- **IP port**: Default: *8443*.

##### Initialization

In order to perform requests, first the **User Name** and **Password** parameters need to be configured.

## How to use

The connector contains the following data pages:

- **General**: Contains the **User Name** and **Password** parameters. If this parameters are not defined, the connector cannot request any data.

- **Alarms**: Contains the **Alarms Filtering Path** parameter, that allows the user to to define a path to an .xml file containing the Fault Filter. This .xml file is used to retrieve only some filtered alarms defined by the user and needs to follow the structure found on the _Nokia NSP XML API Developer Guide_ on chapter **11.6.2**. If there is no defined path to the .xml file or the file does not follow the correct structure, the connector will retrieve all alamrs present on the system. Also on the **Alarms** page there us available the **Alarms** table containing the retrieved information.

- **Probable Cause Configuration/Alarm Name Configuration/Alarm Type Configuration**: On the **Alarms** table columns **Probable Cause/Alarm Name/Alarm Type** by default, what is retrieved form the device, are the IDs of the respective columns.
   On these configuration pages it is possible to define descriptions to these IDs, to be shown on the **Alarms** respective columns. Using the **Probable Cause Configuration** page as example, to **Add** a new entry to the **Alarm Probable Cause** table first **Alarm Probable Cause ID** and **Alarm Probable Cause Description** parameters need to be filled (both of these parameters need to be unique). After defining the parameters the button **Add entry** must be pressed. To **Edit** one description it is possible to do it on the **Description** column itself. To **Remove** one entry it is possible to do it on the **Delete Entry** button present on the table.

- **Polling Configuration**: On this page, you can select which of the available requests is polled and when. You can also poll the requests on demand with the **Poll** button for each entry in the table.
