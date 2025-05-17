---
uid: Connector_help_F5_OS_Appliance_Technical
---

# F5 OS Appliance

The F5 OS Appliance connector facilitates the monitoring of the F5 rSeries devices by centralizing and displaying its most critical information.

The F5 rSeries is a hardware device that acts as an Application Delivery Controller (ADC). It's used to manage and optimize the delivery of applications to users.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |F5OS-A R5R10 1.8.0-17564  |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: The IP Address of the device where its API will be available
  - **IP port**: IP Port used to communicate with API (default: *8888*)
  - **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.


### Initialization

When the element is created, additional configuration must be made in order to start polling information

#### General Page

- **API User Name**: Username used in basic authentication for the API
- **API Password**: Password used in basic authentication for the API

## How to use

After initialization is completed and credentials are valid, the connector will automatically poll all the information available in the API into the pages:

- **CPU**: Contains all the information about the CPU Utilization as well as information for the CPU Processors.
- **Storage**: Contains information of the disks.
- **Hardware**: Contains information about the system memory and system temperature.
	- **FGPA**: Contains information about the Field-Programmable Gate Array.
	- **Fan Tray**: Contains information about the system fans.
	- **Platform Firmware**: Contains information about the firmware of the platforms available.
- **Interfaces**: Contains information about the interfaces and ports.
- **Tenants**: Contains information about the tenants available in the system.