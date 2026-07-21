---
uid: Connector_help_Skyline_EPM_Platform_FTTH
---

# Skyline EPM Platform FTTH

## About

The **Skyline EPM Platform FTTH** connector allows the aggregation of KPIs from different collector elements deployed for different types of infrastructures.

This is an **Experience and Performance Management** connector, and as such it is designed to handle large amounts of data from the deployed infrastructures.

This same connector is used as the frontend element of the EPM Solution and also as a backend element. A deployed EPM Solution contains one Skyline EPM Platform FTTH frontend element and can have one or multiple backend elements. The frontend element is responsible for the top-level data aggregation from different backend elements. Each backend element is responsible for the aggregation of the data from the collectors.

Different topologies are presented in this connector. These topologies are diagrams shown in Visual Overview, which describe the connections between the entities of the different infrastructures. The current implementation integrates the Quick topology which allows you to quickly access the passive topology level by selecting the desired filter (**OLT**, **POP**, **Label**, **ONT**).

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

When you create a Skyline EPM Platform FTTH element, you need to configure the following data:

- Define the **File Import Path** on the Configuration page. This same directory must be configured on all the elements of the EPM Solution.
- Add the frontend, backend, and collector elements on the **FE/BE Registration** page.

### Provisioning

The provisioning of the EPM Solution is sequential and involves the following components:

- **Skyline EPM Platform FTTH** as frontend element: Responsible for the top-level data aggregation and for displaying the topologies.
- **Skyline EPM Platform FTTH** as backend element: In charge of the data aggregation from the collectors.
- **Skyline EPM Platform FTTH Collector**: In charge of the ONT data aggregation from an OLT.
- **Telenet EPM Platform FTTH WM**: Creates compatible files regarding the passives available within the GPON infrastructure and the KAFKA OLT KPIs.

## How to use

The solution is based on the usage of **CSV** files.

The implemented architecture has a central point of control where the frontend element notifies, using Inter-App messages, all the Workflow Managers in the DMS to generate the structured files for each entity. After that, the remaining blocks (collectors and backend elements) are informed to ingest them.

A new provisioning process is initiated when you click the provision button in the frontend element. This action triggers a sequence of events spaced at 5-second intervals.

1. The Workflow Manager elements are notified to generate the structured files with the IDs for each entity. Once these have been generated/exported, the frontend element is notified of this.
1. The collector elements are notified to import the files.
1. The backend elements are notified to import the files.

By default, the destination is expected to respond within 5 seconds, but this polling interval can be customized with the timer base option.

Since all blocks report to the frontend element, if one block fails to respond, the source of the failure can immediately by identified.
