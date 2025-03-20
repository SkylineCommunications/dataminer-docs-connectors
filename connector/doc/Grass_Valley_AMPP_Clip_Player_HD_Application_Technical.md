---
uid: Connector_help_Grass_Valley_AMPP_Clip_Player_HD_Application_Technical
---

# Grass Valley AMPP Clip Player HD Application

## About

The Clip Player HD  is an application connector defined for the GV AMPP (Agile Media Processing Platform) solution, designed to show the status and allow the configuration of the workloads added to a fabric in AMPP. It depends on InterApp messages from the Grass Valley AMPP Manager.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).

## Usage

The following data pages are available in an element created with this connector:

- **General**: Contains the **Overview** and **States** tables. The Overview table shows the workloads for the Clip Player HD Input type, and the States table allows you to send Start, Stop, GoToStart, GoToEnd,  HTTP commands as well as change the File Name of each workload. Note: since the File name is retrieved from the interapp, but the start of the path is not, user must additionally configure the File Path (the beginning part of the file name) for the command to work.
- **Debug**: Enabled by a toggle button at the bottom of **General** page, this page includes the Last Login Time, Token Expiration, Response Status Code, and Manager Element Name.
