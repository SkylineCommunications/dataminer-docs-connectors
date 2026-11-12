---
uid: Connector_help_Skyline_Service_Management_Mediation_Technical
---

# Skyline Service Management Mediation

## About

The Skyline Service Management Mediation connector is a virtual connector responsible for executing the export and import automation scripts for Service Management. It ensures that export and import operations are executed sequentially, preventing multiple operations from running simultaneously, while providing visibility into the status of both ongoing and most recently completed operations.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

After the element has been created, register the export and import automation scripts it needs to run in the **Export Scripts** and **Import Scripts** tables on the **General** page. See [Export Scripts](#export-scripts) and [Import Scripts](#import-scripts) below.

## How to Use

### General Page

This page shows the state of the mediation action:

- **Mediation Action**: The operation that is currently running: *Idle*, *Importing*, or *Exporting*.
- **Last Executed Script**: The name of the script or request that was executed last.
- **Last Operation Status**: The result of the last operation: *Succeeded* or *Failed*.
- **Last Operation Timestamp**: The time when the last operation finished.
- **SMG Configuration Parameters Page**: Shows or hides the **Configuration Parameters** page.

Only one export or import operation can run at a time. While **Mediation Action** is not *Idle*, new export and import requests are rejected.

#### Export Scripts

The **Export Scripts** table contains the automation scripts that export service data. Each row has a unique **Description**, the name of the **Script**, the output **Directory**, and optional **Extra Input Parameters**.

Right-click the table to:

- **Run Script**: Run the selected export script.
- **Add Script**: Add a script by entering a description, the script name, and the output directory. The description must be unique.
- **Edit Script**: Change the description, script name, or directory of the selected script.
- **Remove Script**: Remove the selected scripts after confirmation.
- **Edit Directory**: Change the output directory of the selected script. The directory must exist on the DataMiner Agent.
- **Add/Update Input Parameter**: Add an extra input parameter with a name and value to the selected script, or update the value of an existing one.
- **Remove Input Parameter**: Remove an extra input parameter from the selected script by entering its name.

When an export script is run, the connector passes the following script parameters to it:

- **File Path**: The directory configured for the script.
- **Extra Parameters**: The extra input parameters of the script, in JSON format.

#### Import Scripts

The **Import Scripts** table contains the automation scripts that import service data. Each row has a unique **Description** and the name of the **Script**.

Right-click the table to **Run Script**, **Add Script**, **Edit Script**, or **Remove Script**. Import scripts are run without input parameters.

### Configuration Parameters Page

This page is hidden by default. To show it, set **SMG Configuration Parameters Page** on the **General** page to *Visible*.

- **Service Order ID**: The next service order ID that will be issued.
- **Service ID**: The next service ID that will be issued.

These values are read-only. They are increased when IDs are reserved through the Service Management application.