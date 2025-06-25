---
uid: Connector_help_iDirect_Evolution_VSAT_Terminal_Provisioning
---

# iDirect_Evolution VSAT Terminal Provisioning

The iDirect Evolution VSAT Terminal Provisioning connector can be used to configure and provision terminals on a iDirect Evolution Platform NMS.
This platform is an IP-based satellite communication system, with a product line consisting of a universal hub and network management system.
It consists of a series of line cards, operating software, and a portfolio of both dedicated and dual-mode remotes.
It interacts with the iBuilder Software API to execute configuration and provisioning commands on the mentioned system.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |4.6.1.0        |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination. (default: *443*)
  - **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.


### Initialization
After creating a new element it is necessary that the user specifies the login credentials in the Authentication page

## How to use

In the **Provisioning** page there are two sections that can be used to provision a single or multiple terminal(s).
An existing configuration template can be loaded by specifying the terminal ID that contains the settings the user wants to load.
The single terminal provisioning section can be used to execute the specified button action with the provided configuration settings (Terminal Configuration).
The bulk terminal provisioning section (Bulk Actions) will sequentially configure a given amount of terminals based on the selected configuration settings template (Terminal Configuration).

