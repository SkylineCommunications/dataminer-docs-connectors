---
uid: Connector_help_Skyline_Service_Management_Mediation
---

# Skyline Service Management Mediation

## About

The Skyline Service Management Mediation connector is a virtual connector that serves as a central execution point for Service Management automation scripts. It handles the export of service data from and the import of service data into the DataMiner system.

## Key Features

- **Central export and import script management**: Export and import automation scripts are registered in tables on the element and can be run, added, edited, or removed via the context menu.

- **Sequential operation execution**: The connector makes sure that only one export or import operation runs at the same time. Requests that arrive while an operation is in progress are rejected.

- **Operation status monitoring**: The current mediation action, the last executed script, and the status and time of the last operation are displayed on the element and can be alarmed and trended.

## Use Cases

### Exporting Service Data on Request

**Challenge**: Several users or scripts may want to export service data at the same time, which can result in conflicting or incomplete export files.

**Solution**: All export scripts are started through the connector, which only allows one operation at a time and rejects other requests while an export is running.

**Benefit**: Exports never overlap, and the element always shows which export is running and how the last one ended.

### Importing Services From an External Source

**Challenge**: Services from an external source need to be imported into DataMiner Service Management in a controlled way.

**Solution**: An import script registered on the element, or an InterApp import request, imports the service data while the connector tracks the progress and result of the operation.

**Benefit**: Imports are serialized and their result is visible on the element.

## Technical Reference

### Prerequisites

- The export and import automation scripts that the connector needs to run must be available in the DataMiner system.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Skyline_Service_Management_Mediation_Technical).
