---
uid: Connector_help_Generic_Logger_Table
---

# Generic Logger Table

The Generic Logger Table is a virtual connector that allows DataMiner solutions to interact directly with a table in the underlying database.

Every element using this connector will have its own unique table in the database. The connector handles incoming CRUD operations and automatic cleanup.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

As soon as an element is created, it automatically generates a new table in the database.

With the **Remove Unmodified Entries After** parameter on the **General** page of the element, you can adjust how long each record is stored in the table. By default, this is set to 30 days.

## How to Use

Manipulating the data handled by the element is done using the [Skyline.DataMiner.ConnectorAPI.GenericLoggerTable NuGet package](https://github.com/SkylineCommunications/Skyline.DataMiner.ConnectorAPI.GenericLoggerTable). This package is typically used from automation scripts, but it can also be used from connectors.

### Supported Operations

The connector and NuGet package support the typical CRUD operations: creating, replacing, updating and removing records.

### Use Case

The typical use case for this connector is to store large pieces of data that do not need to be directly accessible from Cube. As such, there is no way to monitor the data.
