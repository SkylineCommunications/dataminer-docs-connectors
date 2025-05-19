---
uid: Connector_help_F5_OS_Appliance_Technical
---

# F5 OS Appliance

## About

The F5 OS Appliance connector facilitates the monitoring of the F5 rSeries devices by centralizing and displaying the most critical information.

The F5 rSeries is a hardware device that acts as an Application Delivery Controller (ADC). It is used to manage and optimize the delivery of applications to users.

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |F5OS-A R5R10 1.8.0-17564  |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The IP address of the device where its API will be available.
- **IP port**: The IP port used to communicate with API (default: *8888*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

When the element is created, configure the following parameters on the **General** page in order to start polling information:

- **API User Name**: Username used in basic authentication for the API.
- **API Password**: Password used in basic authentication for the API.

## How to use

After valid credentials have been specified, the connector will automatically poll the information available in the API and display it in the element on the following pages:

- **CPU**: Information about the CPU utilization and the CPU processors.
- **Storage**: Information about the disks.
- **Hardware**: Information about the system memory and system temperature.

  - **FGPA**: Information about the Field-Programmable Gate Array.
  - **Fan Tray**: Information about the system fans.
  - **Platform Firmware**: Information about the firmware of the available platforms.

- **Interfaces**: Information about the interfaces and ports.
- **Tenants**: Information about the tenants available in the system.
