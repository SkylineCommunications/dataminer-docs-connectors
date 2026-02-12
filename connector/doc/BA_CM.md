---
uid: Connector_help_BA_CM
---

# BA CM

## About

The **BA CM** connector interacts with a **WFM** from where an entire system can be set up and created in DataMiner.

This connector is part of a multiple connectors and a **WFM**.

Via the **WFM**, the **BA CM** connector will receive commands to build up an entire system in DataMiner. This includes a **view**, **services**, **elements**, **correlation rules**, **RCA**, etc.

The tree structure and configuration details are found and saved in a custom database. In here, there are two types of tables: **Remedy** and **DataMiner**. The **Remedy** tables contain the structure, while the **DataMiner** tables will contain all of the changes that were done via the **WFM**. For example, creation of a new equipment will add a row in the **DataMiner-Equipment** table.

## Installation and configuration

## Creation

This is a **virtual** connector, so no device info needs to be configured on creation of the element.

### Database Connection

All of the info needed by the **WFM** is stored in a custom database. The connection info needs to be entered in the **Server Info Page** via the **Database Login** page button.

### DataMiner Login Info

As multiple specific DataMiner items need to be created in the system, e.g. **RCA** and **correlation rules**, a **Login** needs to be defined that will be used to add these items. This is done via the **Login Info** page button.

## CM Config

In order to have the connector execute all of the **WFM** requests correctly, some additional settings need to be done via the **CM Config** page button.

## Usage

This connector is used by the WFM. Only a few actions can be done via the element itself.

## General Page

From here, it is possible to check the database connection and set the configurations via the page buttons mentioned under Installation and configuration.

There is also an extra **Toolbox** that includes some buttons to force execute some settings on the entire system, which are normally done one by one via the **WFM**. As these button will perform actions on the entire system, it is possible that this will slow or block it for the time needed to process the request. For example, **Create RCA** will create all of the **RCA** in the system. Be careful using these buttons.

Other displayed items are used as information during an update of the system via the **WFM.** Via the **UpdateRMU**, **Create Template** and **UpdateCorrel** tables, it is possible to check what the BA CM connector is currently executing after a "load on system" command was sent by the WFM.

## Notes

There are three fixed types of equipment than can be created:

- Moscad: protocol **Motorola Moscad**
- ACTTS: protocol **BA ACTTS**
- TBox: protocol **Semaphore TBox** range **2.x.x.x**

For these types, the BA CM will forward the WFM Command to the elements using the correct protocol.
