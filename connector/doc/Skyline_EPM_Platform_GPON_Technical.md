---
uid: Connector_help_Skyline_EPM_Platform_GPON_Technical
---

# Skyline EPM Platform GPON

## About

The **Skyline EPM Platform GPON** connector allows the aggregation of KPIs from different platform elements of the GPON infrastructures. This connector is an Experience and Performance Management connector, and as such it is designed to handle large amounts of data from the GPON infrastructures.

**Skyline EPM Platform GPON** is a **back-end** connector compatible with the **Skyline EPM Platform Solution**. A deployed EPM Solution contains one [Skyline EPM Platform](xref:Connector_help_Skyline_EPM_Platform) **front-end** element, but it can have one or multiple **Skyline EPM Platform GPON back-end** elements.

The Skyline EPM Platform front-end element is responsible for the top-level data aggregation from different back-end elements, while each back-end element is responsible for the aggregation of the data from the OLT Platform elements. The following OLTs are available: [ZTE ZXA10 C600 GPON Platform](xref:Connector_help_ZTE_ZXA10_C600_GPON_Platform), [Huawei 5600-5800 GPON Platform](xref:Connector_help_Huawei_5600-5800_GPON_Platform), and [Nokia ISAM 7300 FX GPON Platform](xref:Connector_help_Nokia_ISAM_7300_FX_GPON_Platform)

Different topologies are presented in the **Skyline EPM Platform**. For the GPON infrastructure, the following chains are present:

- **GPON Service:**

  - Network
  - Market
  - Hub
  - OLT
  - Slot
  - Port
  - ONT

- **Quick**

  - Split Route, Split Distribution, Split FAT

- **Configuration**

  - Allows you to place Visual Overview layouts on a separate chain.

The KPIs in the topologies are the result of aggregation performed in the **Skyline EPM Platform GPON back-end** elements.

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [Obsolete] | Initial version | - | - |
| 1.0.1.x [Obsolete] | Quick topology for GPON now contains Split Route, Split Distribution, Split FAT. Generic Split level was removed. | - | - |
| 1.0.2.x [Obsolete] | Removed remote view for ONT level | - | - |
| 1.0.3.x [Obsolete]  | The OLT/Slot/Port/Split Route/Split Distribution/Split FAT Overview tables now include new Rx Power states to provide more specific and accurate status information. | 1.0.2.7  | Tables IDs changed. |
| 1.0.4.x [SLC Main]  | The GPON functionalities from the [front-end connector](xref:Connector_help_Skyline_EPM_Platform_Technical) have been migrated to this one. | 1.0.3.1  | Front-end functionalities included. |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | No | Yes | Automation scripts: <br>- EpmBeToOlt <br>- EpmBeToOltPassives <br>Generic KAFKA Consumer Connectors: <br>- ZTE ZXA10 C600 GPON Platform <br>- Huawei 5600-5800 GPON Platform <br>- Nokia ISAM 7300 FX GPON Platform <br>- Skyline EPM Platform | - |
| 1.0.1.x | No | Yes | Automation scripts: <br>- EpmBeToOlt <br>- EpmBeToOltPassives <br>Generic KAFKA Consumer Connectors: <br>- ZTE ZXA10 C600 GPON Platform <br>- Huawei 5600-5800 GPON Platform <br>- Nokia ISAM 7300 FX GPON Platform <br>- Skyline EPM Platform | - |
| 1.0.2.x | No | Yes | Automation scripts: <br>- EpmBeToOlt <br>- EpmBeToOltPassives <br>Generic KAFKA Consumer Connectors: <br>- ZTE ZXA10 C600 GPON Platform <br>- Huawei 5600-5800 GPON Platform <br>- Nokia ISAM 7300 FX GPON Platform <br>- Skyline EPM Platform | - |
| 1.0.3.x | No | Yes | Automation scripts: <br>- EpmBeToOlt <br>- EpmBeToOltPassives <br>Generic KAFKA Consumer Connectors: <br>- ZTE ZXA10 C600 GPON Platform <br>- Huawei 5600-5800 GPON Platform <br>- Nokia ISAM 7300 FX GPON Platform <br>- Skyline EPM Platform | - |
| 1.0.4.x | No | Yes | Automation scripts: <br>- EpmBeToOlt <br>- EpmBeToOltPassives <br>Generic KAFKA Consumer Connectors: <br>- ZTE ZXA10 C600 GPON Platform <br>- Huawei 5600-5800 GPON Platform <br>- Nokia ISAM 7300 FX GPON Platform | - |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Before the creation of a **Skyline EPM Platform GPON** element it is necessary to install the Automation Scripts **EpmBeToOlt** and **EpmBeToOltPassives** (without these scripts, the element will not function).

All components of the **Skyline EPM Platform Solution** work with a file system for internal communication. Because of this, when a new **Skyline EPM Platform GPON** element is created, the following parameters must be defined on the **Configuration** page:

1. Element Role (from 1.0.4.x onwards)

   On the Configuration page, you need to define if the element will act as *Backend* or *Frontend*. Initially, this parameter is set to "Not Defined" to avoid executing processes from an undesired role.

1. Import Settings

   - **Entity Import Directory**: Specify the generic GPON entity import path that is used throughout the EPM Solution. From this path, the **Skyline EPM Platform GPON** will retrieve the OLT topology CSV file.

   - **Entity Import Directory Type**: Specify whether the import path is local or remote. Note that for the remote file handling to work, the credentials for the system must be entered in the **System Credentials** section and the directory must be set to a remote path. The path has to be shared/accessible, or this feature will not work.

1. Export Settings

   - **Entity Export Directory**: Specify the generic GPON entity export path that is used throughout the EPM Solution.

   - **Entity Import Directory Type**: Specify whether the respective export path is local or remote. Note that for the remote file handling to work, the credentials for the system must be entered in the **System Credentials** section and the directory must be set to a remote path. The path has to be shared/accessible, or this feature will not work.

1. System Credentials: This section is to be used if the element is configured to a remote file location.

   - **System Username**: The username that has access to the remote directory. If no domain is specified, the domain from the element's DMA location will be used.

   - **System Password**: The password of the user to access the remote directory.

1. Element registration (from 1.0.4.x onwards): The elements have to be registered using the format **DMA_ID/Element_ID**, and this process depends on whether the element has been set as *Backend* or *Frontend*.

   1. **Backend**: On the **Collectors Registration** subpage, in the **GPON Collector Registration** table, register the **OLT elements** that will be taken into account for the solution.

   1. **Frontend**: On the **Backends and Collectors Registration** subpage, register the **back-end elements** in the **Backend Registration GPON** table, the **OLT elements** in the **GPON Collector Registration** table, and the front-end element itself in the **Frontend Registration** table.

## How to Use

While this connector is mostly self-reliant once the initial setup is done, there are actions the user can perform.

- The **Provision button** will import all the provisioning files generated by the **Skyline EPM Platform** element and then notify the **OLT** elements to perform the import.

- The **Reset button** removes existing data from tables and performs provisioning logic to remove any erroneous data.

## Notes

### Inner Workflow of the EPM Solution

The provisioning of the EPM Solution for GPON is sequential and involves the following components:

- **Skyline EPM Platform**: Responsible for the top-level data aggregation, displaying the topologies and ID assignment of all entities.
- **Skyline EPM Platform GPON**: In charge of the data aggregation from the OLTs.
- **OLT Platform**: In charge of polling data from the different OLTs (e.g. ZTE ZXA10 C600 GPON Platform) and exporting all available the entities.

> [!NOTE]
> From branch 1.0.4.x onwards, the Skyline EPM Platform is no longer needed, as the Skyline EPM Platform GPON connector can take both the *Backend* and the *Frontend* role.

The solution is based on the usage of CSV files and the DataMiner messaging system:

1. The **OLT elements** export the necessary files containing the resources (GPON topology and passives topology) that need to be assigned DataMiner IDs, and they notify the Skyline EPM Platform GPON front-end element.
1. The **Skyline EPM Platform GPON front-end element** initiates the ID assignment process. The ID request notifications are handled in a FIFO (First-In-First-Out) fashion to ensure the sequential processing of requests.
1. The **front-end element** imports the CSV files to perform the necessary steps of the provisioning.
1. Once the ID assignment is completed, the **front-end element** exports a series of CSV files for the Skyline EPM Platform GPON back-end and OLT elements to import, and it notifies the back-end element to process these files.
1. The **back-end element** imports the resources with their assigned IDs and notifies the respective OLT elements of ID assignment completion.
1. The **OLT elements** import the new files.
