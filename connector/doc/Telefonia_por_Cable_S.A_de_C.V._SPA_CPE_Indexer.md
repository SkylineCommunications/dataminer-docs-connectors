---
uid: Connector_help_Telefonia_por_Cable_S.A_de_C.V._SPA_CPE_Indexer
---

# Telefonia por Cable S.A de C.V. SPA CPE Indexer

This connector is capable of collecting cable modem and ONT data defined in a Skyline EPM Solution that is distributed over multiple clusters.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to use

On the **General** page, you need to provide basic information to enable the retrieval and storage of cable modem and ONT data.

The General page also contains the **Configuration Table**. In this table, you need to create a row (By selecting *Add row* in the right-click menu) for each **Type** and **Domain** from which the data must be collected. The following data must be filled in for each row:

- **Type**: Select *ONT* or *MAC*, depending on the type of data that should be collected.
- **Domain**: Define the system domain. If the data is located locally, mark this field as *N/A*.
- **Directory**: The generic path where the DOCSIS or GPON folder is located. Do not include the domain if the directory is remote. For example: `\DataMiner EPM\DOCSIS`.
- **Directory Type**: Define if the directory is remote or local.
- **System User**: The username that will be used to access the ONT or MAC data. Do not include the domain if the directory is remote. If the directory is local, set the value to *N/A*.
- **Password**: The password that will be used along with the defined System User to access the ONT or MAC data. If the value is local, set the value to *N/A*.
- **Front End Element**: The DMA ID/element ID of the corresponding front-end element.
- **Front End IP**: The IP address of the corresponding front-end server.
