---
uid: Connector_help_TDF_Helios_Database
---

# TDF Helios Database

This connector contains an automatic provisioning solution built for the TDF DVB-T monitoring project. It queries an Oracle SQL database, more specifically the Helios database, to fill in several tables with information about sites, CAT, points of service, and equipment.

Based on these tables, each operator can automatically create views, services, and elements present in the database.

Each operator will have their own exported component and will be able to provision independently from others, with specific filter conditions.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [Obsolete] | Initial version. | - | - |
| 1.0.1.x [Obsolete] | Service views are now created as DataMiner services. | 1.0.0.25 | Instead of only views, services are now also created. |
| 1.0.2.x [Obsolete] | Element provisioning now relies on HOST_IP_ADDRESS and on PNO_CODE. | 1.0.1.54 | Instead of only on HOST_IP_ADDRESS, element provisioning relies on HOST_IP_ADDRESS and on PNO_CODE. |
| 1.0.3.x [Obsolete] | Names of required views in DMS "01 - CAT", "CAT-Elements", "02 - Transport FR3 remontées", and "Transport FR3 remontées-Elements" changed to "01 - F3 CAT", "F3 CAT - Elements", "02 - F3eDliveR", and "F3 eDliveR-Elements", respectively.| 1.0.2.10 | Required views must have the new correct name for the connector to work. |
| 1.0.4.x [SLC Main] | New required views added: "03 -F3 FTR VAISE CDE" and "F3 FTR VAISE CDE-Elements" | 1.0.3.10 | New required views need to be created to the connector to work. |

### Product Info

| Range     | Supported Firmware         |
|-----------|----------------------------|
| 1.0.0.x   | Oracle SQL Developer 1.5.5 |
| 1.0.1.x   | Oracle SQL Developer 1.5.5 |
| 1.0.2.x   | Oracle SQL Developer 1.5.5 |
| 1.0.3.x   | Oracle SQL Developer 1.5.5 |
| 1.0.4.x   | Oracle SQL Developer 1.5.5 |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | No | Yes | - | [TDF Helios Database - Operator](xref:Connector_help_TDF_Helios_Database_-_Operator) |
| 1.0.1.x | No | Yes | - | [TDF Helios Database - Operator](xref:Connector_help_TDF_Helios_Database_-_Operator) |
| 1.0.2.x | No | Yes | - | [TDF Helios Database - Operator](xref:Connector_help_TDF_Helios_Database_-_Operator) |
| 1.0.3.x | No | Yes | - | [TDF Helios Database - Operator](xref:Connector_help_TDF_Helios_Database_-_Operator) |
| 1.0.4.x | No | Yes | - | [TDF Helios Database - Operator](xref:Connector_help_TDF_Helios_Database_-_Operator) |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses Oracle.ManagedDataAccess, a .Net NuGet Managed Driver, to access an Oracle database. No connections need to be configured during element creation.

### Initialization

When the element has been created, go to the **General** page to configure the connection. You will need to define the **Server IP**, **Server Port**, **Username** and **Password**, and **SID**. Depending on your database configuration, the password can be empty. All other parameters must be filled in.

Note that this configuration will only be used to connect to the database when at least one query has been configured. As long as no queries have been configured, the connector will not try to connect.

## How to use

Aside from the **General** page, which contains the connection parameters mentioned above, this connector has a page for each type of query.

### Queries

On the **Sites**, **CAT**, **Point of Services**, and **Equipments** pages, you need to define the **"Query name" Query File Path**. This is the path to the file where the query is available. This file must contain the **partial query** from the **"from"** keyword onwards, including the "from" keyword itself (see [example](#example-of-a-sites-query-file) below). The initial part of the query is initialized by the connector itself. This part is fixed, and the columns of the tables depend directly on it.

After you have created the query file and configured the relevant Query File Path parameter, you can execute the query with the **Execute "Query Name" Query** button.

The **Execute State "Query Name" Query** indicates the current status of a query:

- *Running Query*: The query is currently being performed on the database.
- *Filling Table*: The table of the connector is being filled in.
- *Failed*: The query has failed.
- *Success*: The query has been completed successfully.

If a query fails, a **"Query Name" Query Error Message** will be displayed.

These status parameters are available on all query pages, as well as on the General page, where the status of the most recently executed query is displayed.

There are also some parameters that indicate the progress of a query:

- **"Query name" Query Rows Read:** Indicates how many rows of the query have actually been read from the database.
- **"Query name" Table Rows Filled**: Indicates how many rows of the table in the connector have been filled in.
- **"Query name" Last updated**: Indicates the last time and date when this query was updated.
- **"Query Name" Count**: Indicates how many rows the table actually contains.

Finally, on the different query pages, the tables with the query results are also displayed.

### Example of a Sites query file

*"from*
*Q_helios_publication.sio_site,* *(select distinct sio_servicet.loc_code_ig from Q_helios_publication.sio_servicet,Q_helios_publication.sio_servicec where* *sio_servicet.cfs_code=sio_servicec.cfs_code_service_client(+)* *and* *( ( cfs_date_arret_realisee is null and CFS_classe='TNT')* *OR* *(* *sio_servicec.cfs_code_service_client is null and* *rfs_statut='Actif'* *and* *rfs_item_de_catalogue like '%TNT%')))* *SERVICE* *where* *sio_site.loc_statut\<\>'ObsolŠte'* *and* *sio_site.loc_code_ig=SERVICE.loc_code_ig*
*order by sio_site.loc_code_ig"*

### Operators

On the **Operators** page, you can use the right-click menu of the Operators table to create new exported components for the operators or delete them. When you create a new exported component, you will need to define a unique name for it.

### Provisioning

There are several general (i.e. common to all operators) provisioning settings available on the **Provisioning** page.

In the **DMA Departments Allocation** table, which contains a row per DMA available in the DMS, you can define DMA allocation, which determines to which DMA the elements from several departments are going to be assigned.

- In the **Departments List** column, you can define which departments will be assigned to that DMA.

- To define which types of services (*All Services* or *Only Standard Services*) will be assigned to the DMA, you need to define the **Metropole Services Segmentation**.

- The **Elements Margin** column is used to define the percentage of elements that will not be create to ensure that the maximum number of elements in the DataMiner license is not exceeded. TDF uses DMAs with a 500 or 1000 elements license.

For each type of protocol to be assigned to the created elements, you can also configure generic settings in the **Element Settings** table.

The service templates that define how the services are going to be created are defined on the **Services Templates** subpage. There are two types of service templates: internal service templates and customer service templates. To define customer service templates, right-click the **Customer Service Templates** table and select the relevant customer. The services will only be created if these service templates settings are assigned.

For more specific information about the provisioning, see [TDF Helios Database - Operator](xref:Connector_help_TDF_Helios_Database_-_Operator).

## Notes

The table rows are updated with 1000 rows at a time. This limitation is in place in order to avoid a possible negative effect on DataMiner performance.
