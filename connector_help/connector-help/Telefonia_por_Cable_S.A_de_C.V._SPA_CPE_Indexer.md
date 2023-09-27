---
uid: Connector_help_Telefonia_por_Cable_S.A_de_C.V._SPA_CPE_Indexer
---

# Telefonia por Cable S.A de C.V. SPA CPE Indexer

This connector is capable of collecting Cable Modens and ONTs data defined in a Skyline EPM Solution that is distributed in multiple clusters.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version  | \-           | \-                |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | \-                    | \-                      |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Redundancy

There is no redundancy defined.

## How to use

In the connector, there is a "General" page where the user must provide basic information to enable the retrieval and storage of Cable Modem and ONT Data.

Within this page, the user is required to set up the **Export Directory** by specifying the local path where the output data will be stored.

Additionally in the General page, the user will find the **Configuration Table**.  

In this table, the user must create a row (right-click, add row) for each **Type** and **Domain** from which the data must be collected. The following data must be filled in for each row:

- **Type**: The user must select ONT or MAC, depending on the type of data that should be collected.
- **Domain**: Define the System Domain. If the data is located locally, the user must mark this field as N/A.
- **Directory**: The generic path where the DOCSIS or GPON Folder is located (Do not include the Domain if Remote). For example: \DataMiner EPM\DOCSIS.
- **Directory Type**: The user must define if the directory is remote or local.
- **System User**: The username that will be used to access the ONT or MAC data (Do not include the Domain if Remote). If the directory is local, the value must be set as N/A.
- **Password**: The password that will be used along with the System User to access the ONT or MAC data. If the value is local, the user must define it as N/A.
- **Front End Element**: The DMAID/ElementID of the corresponding Front End element.
