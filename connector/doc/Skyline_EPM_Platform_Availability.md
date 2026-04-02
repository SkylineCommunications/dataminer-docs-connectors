---
uid: Connector_help_Skyline_EPM_Platform_Availability
---

# Skyline EPM Platform Availability

The Skyline EPM Platform Availability is an EPM Manager that is intended to be used with the **Skyline Platform Collector** connector.

This connector manages all the endpoints and ping statistics from the entire system and maintains relational information and aggregated data that can be viewed from a central front-end element and from the DataMiner Topology app.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

If you use the **EPM Setup Wizard** automation script in the EPM TOOLS folder, the initialization detailed below is handled automatically.

If you create the managers manually without the script, follow these steps:

1. Create a single **front-end element** and configure it as follows:

   1. On the **Configuration** page, change the **Element Manager Type** to *Frontend*.

   1. In the **Import Settings**, fill in the import directory where the MASTER_PING.csv file is located.

   1. In the **Export Settings**, fill in the location from which the **back-end** elements will be importing.

1. Create as many **back-end elements** as needed.

   Typically, the front-end element should be on a DMA of its own, and there should be a back-end element on all other DMAs. If the DMS only consists of one DMA, then it can have one front-end and one back-end element.

1. In the **Import Settings** on the **Configuration** page of the back-end elements, fill in the directory where the front-end element will export.

1. In the **Export Settings** on the **Configuration** page of the back-end elements, fill in the directory from which the collectors will import.

1. In the **front-end** element, fill in the necessary DMA ID/Element IDs:

   - In **Frontend Registration** table, fill in the DMA ID/Element ID of the front-end element.

   - In the **Backend Registration** table, fill in all DMA ID/Element IDs of the back-end elements in the system.

   - In the **Collector Registration** table, fill in all DMA ID/Element IDs of the collector elements in the system.

1. In the **back-end** elements, fill in the necessary DMA ID/Element IDs:

   - In the **Backend Registration** table, fill in the DMA ID/Element ID of the current back-end element.

   - In the **Collector Registration** table, fill in all DMA ID/Element IDs of the collector elements on the **same DMA**.

1. On the **Configuration** page of the *front-end* element, click the **Import** button to begin the provisioning.

## How to use

Once the EPM Manager elements have been configured, the only necessary procedure is for the front-end element to import the MASTER_PING.csv file whenever there is a change to the file.
