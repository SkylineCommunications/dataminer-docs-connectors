---
uid: Connector_help_VOO_Ad_Hoc_Polling
---

# VOO Ad Hoc Polling

## About

The goal of this connector is to poll KPIs from a list of MTAs independently of the CPE (Seram) system.

Multithreaded polling is used to retrieve information from the CMTS using **SNMP** and **SSH**, and from the MTA using **SNMP**.

CMTS elements are automatically detected on the DMS, but you can add custom entries too (to enable polling of MTAs, even if the CMTS element is not present). You can maintain a list of MTAs that have to be polled. The following information must be defined for each MTA: MAC, Description, CMTS (dropdown), Type.

The **IP addresses** of the MTAs are updated periodically with information from the CMTS.

## Configuration

### Connections

This connector uses two SNMP connections and an SSH connection and requires the following input during element creation:

**SNMP CONNECTION (MTA)**:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string in order to read from the device. The default value is *public*.
- **Set community string**: The community string in order to set to the device. The default value is *private*.

**SNMP CONNECTION (CMTS)**:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string in order to read from the device. The default value is *CADMIUM*.
- **Set community string**: The community string in order to set to the device. The default value is *private*.

**SERIAL CONNECTION (CMTS)**:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*.
- **IP port**: The port of the connected device, by default *22*.

### Initialization

When you have created the element, go to the **Configuration** page and specify the SSH credentials of the CMTS.

## Usage

### General page

This page displays a tree view with the CMTS collectors and MTAs.

### CMTS Collectors page

This page provides a table containing all the CMTS collectors that must be polled by this connector. All CMTS collector elements on the DMS are automatically added, but it is possible to manually add entries with the context menu.

### CMTS US Channels Table

This page is hidden by default. On the Configuration page, you can determine whether it should be shown or not.

It displays a table containing all upstream channels on the CMTS. This table is used to link SSH information with SNMP.

### MTA Page

This page provides a table containing all the MTAs that must be polled by this connector. New devices should be added with the context menu.

### MTA Channels page

This page contains a table with upstream channels, and a table with downstream channels, and their information.

### Configuration page

This page contains the configuration parameters used by this element.

### Thread Pool Info page

This page displays information about the thread pools used to poll the devices.

## Notes

A Visio file is available that can be used as a visual overview for easier user interaction.
