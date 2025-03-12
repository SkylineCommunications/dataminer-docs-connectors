---
uid: Connector_help_Ciena_Blue_Planet_Operate_Technical
---

# Ciena Blue Planet Operate

## About

This connector is a network management system designed to manage Ciena devices.

## Configuration

### Connections

#### HTTP Main connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The port of the connected device, by default 60443. (required port to communicate with API)
- **Bus address**: By default *bypassproxy.*

#### SNMP Secondary Connection

This connector uses a Simple Network Management Protocol (SNMP) connection to process incoming traps. It requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Initialization

In the **General** page, the API Key and User Id parameters need to be filled in before polling of data can occur.

If DVEs need to be created automatically after the polling of data, make sure that from the **Device Management** page, the **DVE Auto Creation** option is enabled and the **Default View Name** is filled in.

## How to use (1.0.0.x)

The element created with this connector consists of the following data pages:

- **General**: Displays configuration parameters required for the HTTP requests as well as the **Nodes** tables

  The **Device Elements** subpage displays a table of running DVEs.

- **Device Management**: Displays DVE configuration

- **Alarms**: Displays active alarms from the nodes.

- **Web Interface**: Displays the web interface of the polling IP address.