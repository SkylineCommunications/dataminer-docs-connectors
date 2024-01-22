---
uid: Connector_help_C-COR_CHP_SMM
---

# C-COR CHP SMM

The **C-COR CHP SMM** is used to control and manage the C-COR CHP frame. This element creates dynamic virtual elements (DVEs).

Trending and alarm monitoring are available on many important parameters.

## About

This connector is used to monitor a C-COR CHP frame. It displays the state of the cards, and all the parameters and card configurations.

All the data is polled by **SNMP**. For each module, a **DVE** will be created, which provides an overview of all the information of the connected modules. A list can be found in the section "Exported Connectors".

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 2.0.0.38 | DVE creation based on slot number.<br>Disabled the group polling based on slot number. | No | Yes |
| 2.0.0.39 | Connector review: <br>- Params 30958/30959 and 30965/30966 discreets reviewed. <br>- Normalize page buttons and parameters from pages Normalize removed. <br>- Added a button "Load Names" to load nodes page for setting the Alias parameters from the modules table to the Modules property of the DVEs. <br>- Introduction of disable conditions to parameters 30960-30963 and 30967-30970. <br>- QAction 301 reviewed. | No | Yes |
| 2.0.0.40 | Connector review: <br>- QA100 reviewed for DVE filtering based on bus address. <br>- Implementation of Modules Table filtering (param 100). <br>- New QA3500 and tables 3500-3577 (polling instances) for implementation of subtables logic for restricted polling. | No | Yes |
| 2.0.0.42 | Optical TX Laser Table (Param 2100) (subtable option does not work for the SNMP table):<br>- Added extra Optical TX Laser SNMP Table (Param 2150) without subtable option.<br>- Populated Optical TX Laser Table: use opticalTxLaserFilter to filter data from Optical TX Laser SNMP Table (QA400) <br>Property Table (Param 2500) (subtable option does not work for the SNMP table): <br>- Added extra Property SNMP Table (Param 2550) without subtable option <br>- Populated Property Table: use propertyFilter to filter data from Property SNMP Table (QA67)<br>Update function SetParameters (QA0)</p> | No | Yes |
| 2.0.0.43 | A DVE gets created for every SMM and CMM module in the chassis (for every row in the Shelf table).<br>Those DVEs contain an overview of all the modules in the chassis that are managed by this particular controller card (the rows in the Modules table that correspond with the SMM or CMM module).<br>Added fixes that were made in version 2.0.0.39 and 2.0.0.42. | No | Yes |
| 2.0.0.44 | DVEs are created for all FTX modules (also for DWX modules) | No | Yes |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 2.0.0.x          | Kernel v1.0.6.0             |

### Exported Connectors

| Exported Connector | Description                          |
|--------------------|--------------------------------------|
| C-COR CHP FTX      | Forward path transmitter             |
| C-COR CHP PS MM    | Power supply                         |
| C-COR CHP 2RRX     | Dual return path receiver            |
| C-COR CHP FRX      | Forward path receiver                |
| C-COR CHP RTX      | Optical dual return path transmitter |
| C-COR CHP CMM      | Craft management module              |
| C-COR CHP EDFA     | Optical amplifier                    |
| C-COR CHP GMOD     | Forward transmitter                  |
| C-COR CHP QTX      | Forward path transmitter             |
| C-COR CHP xMM      | SMM and CMM controller card          |

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP Connection:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string needed to read from the device. The default value is *public*.
- **Set community string**: The community string needed to set to the device. The default value is *private*.

> [!NOTE]
> To make the connector only display and poll information for a specific chassis, specify a bus address during element creation.

## Usage

### Main View page

This page contains the **SMM Slot State**, **Slot Uptime** and **Slot Reset Cause**. Aside from these parameters, there is also a **Shelf table** with the status and uptime.

### SMM page

This page contains the main information about the C-COR CHP SMM frame, with the following parameters: **Type**, **Production Date**, **Serial Number**, **Hardware** and **Firmware Version**, **Slot State**, **Slot Uptime**, **Slot Reset Cause**.

There are also some configuration options on this page: **Slot Config Module Front Panel Control** (*Locked* or *Unlocked*), **Module Reset**, **Factory Default**, **Blink LED** and **Reset Slot**.

### Devices page

This page contains a table with all the modules and their module information. There are 8 page buttons: **FTX**, **PS**, **RRX**, **EDFA**, **GMOD**, **RTX**, **FRX** and **QTX**.

Each page button opens a pop-up page containing all module information. For each entry in one of these tables, a DVE element is created containing information related to that specific module of the device.

### Load Nodes page

On this page, you can select a **Nodes CSV File Path** and load the Nodes. You can also refresh the file list with the **Refresh File List** button or setting the Alias Name from the modules table to the Modules Name property of the DVEs with **Load Names** button.

## Notes

For each DVE created, there are pages with all data and information that is relevant to the device module DVE.
