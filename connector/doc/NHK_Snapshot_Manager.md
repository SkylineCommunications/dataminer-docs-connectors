---
uid: Connector_help_NHK_Snapshot_Manager
---

# NHK Snapshot Manager

The NHK Snapshot Manager is a virtual connector designed to take snapshots of elements and create debug elements using created snapshots and debug connectors.

The *NHK_CreateSnapshots* and *NHK_CreateDebugElements* automation scripts are required in order to create snapshots and debug elements. Debug connectors are created using the [protocol debug tools](https://aka.dataminer.services/Protocol_debug_tools).

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

This page displays the Snapshot Manager table, which contains the following parameters: Snapshot File Name, Element Name, Connector Name, Connector Version, Creation Date, Debug Connector Status, Create Debug Connector, Debug Element Status, Create Debug Element, Notes, and Delete Snapshot File.

Within the Snapshot Manager table, the following actions are possible:

- **Create Debug Connector**: Creates a debug connector based on the snapshot file information. The extension of the debug connector version can be specified with the **Connector Version Extension** parameter (the default extension is `debug`).

- **Create Debug Element**: Creates a debug element based on the snapshot file. The new element will have the same name as the snapshot file. The element will be created using the *NHK_CreateDebugElements* automation script.

- **Delete Snapshot File**: Deletes the snapshot file from the system.

This page also has several standalone parameters:

- **Create Snapshot**: Snapshots are created using the Snapshot Creator Wizard and stored in the location specified with the **Snapshot File Location** parameter. The snapshots will be created with the *NHK_CreateSnapshots* automation script.

- **Snapshot File Location**: By default, the file location will be `C:\Skyline DataMiner\Documents\Snapshot Files`.

- **Debug Element View**: This parameter determines which view the debug elements will be created in. If no view is selected, the debug elements will be created in the root view.

- **Connector Version Extension**: This parameter specifies the debug connector version extension, which will be appended to the debug connector version. By default, it is set to `debug`.

### Debug Elements

This page displays the Debug Elements Management table, which lists the debug elements that are present in the system.

Via **Delete Debug Element**, you can remove a created debug element.

### Debug Connectors

This page displays the Debug Connectors Management table, which lists the debug connectors uploaded via the [protocol debug tools](https://aka.dataminer.services/Protocol_debug_tools) or the Snapshot Manager itself. These connectors are used to create debug elements.

If you upload a debug connector using the protocol debug tools, make sure to append the value of the **Connector Version Extension** parameter. If the value is `debug`, append `-debug`. Additionally, make sure to select **Remove Sequence** (available from version 1.0.0.6 onwards).

Via **Delete Debug Connector Version**, you can remove a debug connector version.

### Debug Connector Configuration

This page is used to configure the creation of the debug connector. You can also directly create a debug connector here.

- **Add Write Parameters**: If this option is enabled, the debug protocol will be modified to include write parameters for all read parameters in the protocol.

- **Mark Parameters as Saved**: If this option is enabled, the debug protocol will be modified to mark all parameters as saved.

- **Connector**: This dropdown lists all the connectors that a debug connector can be created for.

- **Connector Version Extension**: This parameter specifies the debug connector version extension, which will be appended to the debug connector version. By default, it is set to `debug`.

- **Debug Connector Creation Status**: This parameter indicates the status of debug connector creation when it is initiated from this page.
