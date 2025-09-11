---
uid: Connector_help_Grass_Valley_AMPP_Clip_Player_HD_Application_Technical
---

# Grass Valley AMPP Clip Player HD Application

## About

The Clip Player HD  is an application connector defined for the GV AMPP (Agile Media Processing Platform) solution, designed to show the status and allow the configuration of the workloads added to a fabric in AMPP. It depends on InterApp messages from the Grass Valley AMPP Manager.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection to communicate directly with AMPP and push configuration commands. The URL is set by any AMPP Manager that utilizes this element to manage the specific visualization and configuration of the AMPP Application type. To create an element, it is necessary to enter a URL; in this case, you can use the value *http://localhost*.

HTTP CONNECTION:

- **IP address/host**:*http://localhost*.
- **IP port**: The IP port of the destination (default:*443*).

### Element Configuration

Once the application element is created, it must be linked to the desired Clip Player workload(s) in any Grass Valley Manager. To accomplish this:

1. Annotate the name of the Clip Player Application element.
2. Open the existing AMPP Manager and filter the Workloads table by the application name "*Densite X Clip List Player HD*"
3. Select a desired workload from the filtered list.
4. Click on the "*Refresh State on Restart*" column to configure the manager to receive notifications of the intended workload.
5. In the "*Element*" column, enter the name of the target application element noted in step 1.
6. The manager should present the "*Element Status (workloads)*" column as active, indicating that the target application element was found available in the system.
7. Press the "*Get State*" button to retrieve and forward the current configuration to the target application element. Confirm that the workload is visualized in the target with its current state.
8. To configure additional workloads for the target application, repeat the process starting from step 2.

> [!NOTE]
> Occasionally, it is necessary to restart the AMPP Manager to force a reconfiguration of the application element. Do this if you notice that the target element times out for a long period.

## Usage

The following data pages are available in an element created with this connector:

- **General**: Contains the **Overview** and **States** tables. The Overview table shows the workloads for the Clip Player HD Input type, and the States table allows you to send *Start*, *Stop*, *GoToStart*, *GoToEnd*, and *HTTP* commands, as well as change the file name of each workload.
  
  Note that as the file name is retrieved using InterApp messages, but the start of the path is not, you will also have to configure the file path (i.e. the beginning part of the file name) for the file name change command to work.
- **Debug**: Enabled by a toggle button at the bottom of **General** page, this page includes the Last Login Time, Token Expiration, Response Status Code, and Manager Element Name.

