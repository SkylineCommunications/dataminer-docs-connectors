---
uid: Connector_help_IEC_60870_5-104_Technical
---

# IEC 60870 5-104

## About

The International Electrotechnical Commission (IEC) defines 60870 standards for telecontrol (supervisory control and data acquisition) in electric engineering and power system automation applications. The **IEC 60870 5-104** protocol provides a communication profile for sending basic telecontrol messages between two systems in electrical engineering and power system automation.

IEC 104 provides the network access to IEC 60870 5-101 using standard transport profiles, delivering IEC 101 messages as application data over TCP, port 2404. It enables communication between a control station (master) and a substation (slave) via a standard TCP/IP network. Communication is based on the client-server model.

DataMiner acts as a master whereas the Remote Terminal Unit (RTU) is the slave. The RTU has an internal Programmable Logic Controller (PLC) with digital and analog IO used to monitor telecom or transmission centers. Among others, energy metrics such as oil pressure and temperature, or access metrics such as control mode, control VCC, etc., can be monitored and controlled.

## Configuration

### Connections

#### Smart-Serial Main Connection

This connector uses a smart-serial connection and requires the following input during element creation:

SMART-SERIAL CONNECTION:

- **IP address/host**: The polling IP of the device, e.g. *192.168.56.201*.
- **IP port**: The IP port of the device, e.g. *161*.
- **Bus address**: The bus address of the device, e.g. *1*.

### Initialization

After the connection is established with the RTU, all the Information Object Addresses (IOAs) are retrieved from the unit. The IOAs are configured in the PLC, where each IOA corresponds to a parameter.

A configuration file must be imported with metadata of the RTU's parameters. The file must be placed in one of the following locations:

- `C:\Skyline DataMiner\Documents\Elements\xxx.xlsx`
- `C:\Skyline DataMiner\Documents\Protocol\yyy.xlsx`

Below you can find an example of a metadata file:

![Capture.GIF](~/connector/images/IEC_60870_5-104_Capture.GIF)

Note that the metadata columns above will be displayed in the Parameter table.

## How to Use

Once the connection is successfully established, the status parameters on the General page will be filled in. At startup, the **Parameter** table on the General page is filled in with digital and analog IOA values. As soon as the metadata file is imported, the remaining columns are filled in, as well as the **Command** table on the Command page.

For the commands, at startup, an initial command known as StartDT is sent. This command indicates to the RTU that data transfer can be initiated. After that, the Interrogation command is sent in order to request all the IOAs present in the RTU. Finally, the TestFR command is periodically sent, which is similar to a ping command.

### General Page

The General page shows the connector status and key parameters.

- **Data Transfer**: The current data transfer state between DataMiner and the RTU.
- **Connection**: The status of the IEC 104 connection. Updated when a TestFR response is received.
- **TCP Connection**: The current TCP socket state.
- **Total Number of Parameters**: For range **1.1.0.x only**. Total number of IOAs retrieved from the RTU.
- **DVE Control Table**: Range **1.0.1.x only**. This table is used to generate DVEs and can also force a station interrogation.
- **Parameter Table**: Range **1.1.0.x only**. This table displays all digital and analog parameters retrieved from the RTU.

### Configuration Subpage

On this subpage, you can configure interrogation command scheduling. A **Reconnect** button is available to close and reopen the TCP socket.

### Import File Subpage

On this subpage, you can trigger an import from a CSV/XLSX file or (in range 1.0.1.x only) a script. The following parameters show information related to this:

- **Current Task**: The status of the import operation.
- **Processing Task**: The current processing step.
- **Metadata Table**: Range **1.1.0.x only**. Displays the imported CSV/XLSX data.

For range **1.0.1.x only**, an **Import Script** section allows you to configure and run an automation script to import data. The following parameters are used for this:

- **Import Status**: Shows the import state: *Pending*, *In Progress*, *Completed*, *Failed*.
- **Device**: Allows you to select "ALL" or any of the available DVEs.
- **Automation Script**: Allows you to select any automation script that exposes the input parameters **ImportElementName** and **RequestGuid**.
- **Import User**: Optional text field for a username used by the automation script.
- **Import Password**: Optional password field to securely store credentials for the automation script.
- **Refresh List**: Refreshes the available devices and automation scripts shown in the dropdowns.
- **Import Script**: Prompts for confirmation and then executes the selected automation script. If no script is selected, a warning is shown.

The selected script is invoked with input parameters **ImportElementName** (the element name), **RequestGuid** (a unique identifier for the request) and **Device** (the DVE's identifier). The script must return the operation result and any returned data via InterApp messages using the same RequestGuid. .

> [!IMPORTANT]
> A script template is available in the GitHub repository [IEC 60870 5-104 Import Script](https://catalog.dataminer.services/details/756cb46f-a5e7-43e0-90fe-a8e6095f069f).

### Command Page (Range 1.1.0.x only)

This page contains a table listing all IOAs that support set actions on the RTU.

### Debug Page (Range 1.0.1.x only)

If the **Debug** option is enabled on the Configuration page, the Debug page becomes visible, showing the following parameters:

- **Current APCI data**: APCI frames for debugging.
- **Parameter table**: Digital and analog parameters retrieved from the RTU.
- **Command**: IOAs available for set actions.
- **Metadata table**: Imported CSV/XLSX metadata
