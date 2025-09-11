---
uid: Connector_help_Grass_Valley_AMPP_SRT_Input_Application_Technical
---

# Grass Valley AMPP SRT Input Application

## About

The SRT Input is an application connector defined for the GV AMPP (Agile Media Processing Platform) solution, designed to show the status and allow the configuration of the workloads added to a fabric in AMPP. It depends on InterApp messages from the Grass Valley AMPP Manager.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection to communicate directly with AMPP and push configuration commands. The URL is set by any AMPP Manager that utilizes this element to manage the specific visualization and configuration of the AMPP Application type. To create an element, it is necessary to enter a URL; in this case, you can use the value *http://localhost*.

HTTP CONNECTION:

- **IP address/host**: *http://localhost*.
- **IP port**: The IP port of the destination (default: *443*).

### Element Configuration

Once the application element is created, it must be linked to the desired SRT Input workload(s) in any Grass Valley Manager. To accomplish this:

1. Annotate the name of the SRT Input element.
2. Open the existing AMPP Manager and filter the Workloads table by the application name "*AMPP INPUT - SRT HD*"
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

- **General**: Contains the **Overview** and **Configuration** tables. The Overview table shows the workloads for the SRT Input type, and the Configuration table allows you to send HTTP commands.
- **Debug**: Enabled by a toggle button at the bottom of the **General** page, this page includes the Last Login Time, Token Expiration, and Response Status Code.
