---
uid: Connector_help_Grass_Valley_AMPP_SRT_Input_Application_Technical
---

# Grass Valley AMPP SRT Input Application

## About

The SRT Input is an application connector defined for the GV AMPP (Agile Media Processing Platform) solution, designed to show the status and allow the configuration of the workloads added to a fabric in AMPP. It depends on InterApp messages from the Grass Valley AMPP Manager.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).

## Usage

The following data pages are available in an element created with this connector:

- **General**: Contains the **Overview** and **Configuration** tables. The Overview table shows the workloads for the SRT Input type, and the Configuration table allows you to send HTTP commands.
- **Debug**: Enabled by a toggle button at the bottom of **General** page, this page includes the Last Login Time, Token Expiration, and Response Status Code.
