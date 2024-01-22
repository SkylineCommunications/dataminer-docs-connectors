---
uid: Connector_help_NHK_Snapshot_Manager
---

# NHK Snapshot Manager

The **NHK Snapshot Manager** is a virtual connector designed to take snapshots of elements and create Debug Elements using created Snapshots and Debug Connectors. NHK_CreateSnapshots and NHK_CreateDebugElements Automation Scripts are required in order to create Snapshots and Debug Elements. Debug connectors are created using Protocol Debug Tools

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

This connector uses a virtual connection and does not need any user information.

## How to use

### General

This page displays the Snapshot Manager table, which contains the following parameters: **Snapshot File Name**, **Connector Name**, **Connector Version**, **Create Debug Element** and **Delete Snapshot File**.

Actions within Snapshot Manager table:
**Create Debug Element**: Creates a Debug Element based on the Snapshot File; the new element will have the same name as the Snapshot File. The element will be created using the NHK_CreateDebugElements automation script.
**Delete Snapshot File**: Deletes the Snapshot file from the System.

This page also has 3 Standalone parameters:
**Create Snapshot**: Snapshots are created using the Snapshot Creator Wizard and stored in the location specified by the **Snapshot File Location** parameter. The snapshots will be created with the NHK_CreateSnapshots automation script.
**Snapshot File Location**: By default, the file location will be 'C:\Skyline DataMiner\Documents\Snapshot Files'.
**Debug Element View**: This parameter determines which view the Debug Elements will be created in; if no view is selected, the Debug Elements will be created in the Root View.

### Debug Elements

This page displays the Debug Elements Management table, which contains the Debug elements that are present.

Actions within Debug Elements Management table:
**Delete Debug Element**: Deletes the created Debug Element.

### Debug Connectors

This page displays the Debug Connectors Management table, which contains the Debug connectors uploaded via the Protocol Debug Tools application. These connectors will be used to create Debug Elements. When uploading a debug Connector using Protocol Debug Tools, make sure to append '-debug' and select 'Remove Sequence' ('Remove Sequence' option is available from version 1.0.0.6).

Actions within Debug Elements Management table:
**Delete Debug Protocol Version**: Deletes the created Debug Protocol version.