---
uid: Connector_help_Skyline_EPM_Platform_Availability
---

# Skyline EPM Platform Availability

The Skyline **EPM Platform Availability** is an EPM Manger to be used with the **Skyline Platform Collector** driver. The driver manages all the endpoints and ping statistics from the entire system and maintains relational information and aggregated data to be viewed from a central **Frontend** element and the DataMiner topology app.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial Version         |-         |-         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

All of the following is handled by the EPM Setup Wizard automation script in the EPM TOOLS folder.

If manually creating the managers the following steps are needed:

1. Create a single **Frontend** element and change the **Element Manager Type** to **Frontend** in the **Configuration** page. Then fill in the **Import Settings** with the import directory in which the MASTER_PING.csv file is located and fill in the **Export Settings** where the **Backend** elements will be importing from.

2. Create however many **Backend** elements are needed. Typically, the **Frontend** element should be on it's own DMA and a Backened element on all other DMA's. If the DMS only consists of one DMA, then it may have the one **Frontend** and one **Backend** element.

3. Fill in the **Import Settings** in the **Configuration** page with the directory where the **Frontend** is exporting and the **Export Settings** with the directory where the **Collectors** will be importing from.

4. In the **Frontend**, fill in the **Frontend Registration** table with the DMA ID/Element ID of the **Frontend** element. Then fill in the **Backend Registration** table with all of the DMA ID/Element ID's of all the **Backend** elements in the system. Finally, fill in the **Collector Registration** table with all of the DMA ID/Element ID's of all the **Collector** elements in the system.

5. For all of the **Backend** elements, fill in the **Backend Registration** table with the DMA ID/Element ID of the current **Backend** element and the **Collector Registration** table with the DMA ID/Element ID's of all the **Collector** elements on the same DMA.

6. Hit the **Import** button on the ****Frontend**** element's **Configuration** page to begin the provisioning.

### Redundancy

There is no redundancy defined.



## How to use

Once the **EPM Manager** elements are configured, the only necesarry procedure is to have the **Frontend** element import the MASTER_PING.csv file whenever there is a change to the file.
