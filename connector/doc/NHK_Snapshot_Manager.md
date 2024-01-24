---
uid: Connector_help_NHK_Snapshot_Manager
---

# NHK Snapshot Manager

The NHK Snapshot Manager is a virtual connector designed to take snapshots of elements and create debug elements using created snapshots and debug connectors.

The *NHK_CreateSnapshots* and *NHK_CreateDebugElements* Automation scripts are required in order to create snapshots and debug elements. Debug connectors are created using the [protocol debug tools](https://aka.dataminer.services/Protocol_debug_tools).

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not need any input during element creation.

## How to use

### General

This page displays the Snapshot Manager table, which contains the following parameters: **Snapshot File Name**, **Connector Name**, **Connector Version**, **Create Debug Element**, and **Delete Snapshot File**.

Within the Snapshot Manager table, the following actions are possible:

- **Create Debug Element**: Creates a debug element based on the snapshot file. The new element will have the same name as the snapshot file. The element will be created using the *NHK_CreateDebugElements* Automation script.
- **Delete Snapshot File**: Deletes the snapshot file from the system.

This page also has several standalone parameters:

- **Create Snapshot**: Snapshots are created using the Snapshot Creator Wizard and stored in the location specified with the **Snapshot File Location** parameter. The snapshots will be created with the *NHK_CreateSnapshots* Automation script.
- **Snapshot File Location**: By default, the file location will be `C:\Skyline DataMiner\Documents\Snapshot Files`.
- **Debug Element View**: This parameter determines which view the debug elements will be created in. If no view is selected, the debug elements will be created in the root view.

### Debug Elements

This page displays the Debug Elements Management table, which lists the debug elements that are present in the system.

Via **Delete Debug Element**, you can remove a created debug element.

### Debug Connectors

This page displays the Debug Connectors Management table, which lists the debug connectors uploaded via the [protocol debug tools](https://aka.dataminer.services/Protocol_debug_tools). These connectors are used to create debug elements.

If you upload a debug connector using the protocol debug tools, make sure to append `-debug` and select "Remove Sequence" (available from version 1.0.0.6 onwards).

Via **Delete Debug Protocol Version**, you can remove a debug protocol version.
