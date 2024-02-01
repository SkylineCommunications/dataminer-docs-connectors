---
uid: Connector_help_Generic_Logger_Table
---

# Generic Logger Table

The **Generic Logger Table** is a virtual connector that allows DataMiner solutions to interact directly with a table in the underlying database.

## About

Every element using this connector will have its own unique table in the database. The connector handles incoming CRUD operations and automatic cleanup.

### Version Info

| **Range** | **Description**        | **DCF Integration** | **Cassandra Compliant** |
|------------------|------------------------|---------------------|-------------------------|
| 1.0.0.x          | Initial version | No                  | Yes                     |

## Configuration

### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

As soon as an element is created, it automatically generates a new table in the database.

The amount of time that each record is stored in the table can be adjusted using the *Remove Unmodified Entries After* parameter. By default this is set to 30 days. It is available on the General page of the element.

## How to Use

Manipulating the data handled by the element is done using the [Skyline.DataMiner.ConnectorAPI.GenericLoggerTable NuGet package](https://github.com/SkylineCommunications/Skyline.DataMiner.ConnectorAPI.GenericLoggerTable). This package is typically used from Automation scripts, but it can also be used from Connectors.

### Supported Operations

The connector and NuGet package support the typical CRUD operations; creating, replacing, updating and removing records.

### Use Case

The typical use case for this connector is to store large pieces of data that doesn't need to be directly accessible from Cube. As such, there is no way to monitor the data.