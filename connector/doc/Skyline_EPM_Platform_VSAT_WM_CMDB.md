---
uid: Connector_help_Skyline_EPM_Platform_VSAT_WM_CMDB
---

# Skyline EPM Platform VSAT WM CMDB

## About

The **Skyline EPM Platform VSAT WM CMDB** connector is a workflow manager that handles file-based provisioning for the CMDB(Customer Management Database) data management within the system.
This connector reads device inventory data from JSON files, processes mapping configurations, and generates provisioning output files for connectors.

## Key Features

- **Automated File Provisioning**: Automatically imports, transforms, and exports inventory data on a configurable interval, reducing manual data management overhead.

- **Flexible JSON Mapping Engine**: Uses a JSON-based mapping configuration that allows field renaming, constant values, nested object creation, array transformation, and default value handling without code changes.

- **Multi-Format Configuration File Support**: Reads Configuration (CC) files in both XML and CSV formats, extracting device names to filter relevant inventory records.

- **Remote File Access**: Supports accessing files from network shares using configurable Windows credentials with impersonation.

- **Dual Import Sources**: Processes both connector-specific and global inventory files, enabling hierarchical data provisioning across different system levels.

## Use Cases

### Use Case 1

**Challenge**: Managing large networks requires synchronizing inventory data from a central CMDB to multiple distributed collectors, each handling a subset of devices.

**Solution**: The connector imports a global circuit inventory JSON file and multiple configuration files (one per collector). It filters inventory records based on device names present in each configuration file and generates collector-specific provisioning (CP) files.

**Benefit**: Automated, targeted provisioning ensures each collector receives only the relevant data, reducing network overhead and processing time while maintaining data consistency across the system.

### Use Case 2

**Challenge**: The source CMDB exports data in a different structure than what the downstream collectors expect, requiring field transformations, renaming, and restructuring.

**Solution**: The JSON mapping file allows operators to define transformations declaratively: copying fields with `from`, setting constants with `const`, creating nested objects using dot notation, transforming arrays with `itemFields`, and providing fallback values with `default`.

**Benefit**: Data structure changes can be accommodated by updating the mapping file without modifying connector code, reducing deployment time and testing effort for schema changes.

### Use Case 3

**Challenge**: Inventory files are stored on remote network shares that require authentication, and different environments may use local or remote storage.

**Solution**: The connector provides configurable directory type settings (Local/Remote) for both import and export paths, along with username and password parameters for Windows credential-based impersonation when accessing remote shares.

**Benefit**: Flexible deployment options allow the same connector to work in different network topologies, from standalone servers with local files to distributed environments with centralized file shares.

## Technical Reference

### Prerequisites

- **DataMiner Version 10.3.0.0 - 12752 or higher** is required as specified in the connector's minimum required version.

- **Configuration (CC) Files** are needed in XML or CSV format containing device names under `Remotes/Remote/Name` (XML) or a `Name` column (CSV) to filter inventory records.

- **Mapping Configuration File** is required to define how source inventory fields are transformed into output fields. See the [technical documentation](xref:Connector_help_Skyline_EPM_Platform_VSAT_WM_CMDB_Technical) Mapping JSON File section for configuration details.

- **Global Inventory JSON File** containing a `records` array with device data for the entire system.

- **Network Credentials** are required when using remote directory types for import/export paths (domain\username format supported).

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Skyline_EPM_Platform_VSAT_WM_CMDB_Technical).

