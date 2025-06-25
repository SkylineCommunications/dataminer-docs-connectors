---
uid: Connector_help_Double_D_Electronics_DDA289_Technical
---

# Double D Electronics DDA289

The connector monitors the activity of the Double D Electronics DDA289 Redundancy Controller.

## About

The connector uses a serial communication to the Double D Electronics DDA289 and allows the end user to switch positions and view the status of the device's converters.

The connector utilizes three polling intervals to gather data at different rates:

1) Every 5 seconds – captures rapidly changing information, such as switch positions and converter statuses.
2) Every 1 minute – retrieves the summary status of the controller.
3) Every 1 hour – collects data that changes infrequently, such as controller configuration data.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x          | Initial version | No                  | Yes                     |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | DDA289 V0.11                |

## Installation and configuration

### Creation

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: Baudrate specified in the manual of the device, e.g. *9600.*
  - **Databits**: Databits specified in the manual of the device, e.g. *7.*
  - **Stopbits**: Stopbits specified in the manual of the device, e.g. *1.*
  - **Parity**: Parity specified in the manual of the device, e.g. *No.*
  - **FlowControl**: FlowControl specified in the manual of the device, e.g. *No.*

- Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: The bus address of the device.

## Usage

The connector has three pages: 1) General, 2) Switches, and 3) Converters.

### General Page

The General page displays key information about the device on the left side, including: **Unit Type**, **Software Version**, **Number of Supported Paths**, **Number of Switch Banks Fitted**, **Equipment Name** and **Configuration Version**.

Additionally, users can set the **Global Device Mode** and its corresponding  **Control Mode**.

On the right side, the page shows the status of any alarms or power supply issues, including:  **Primary Alarms**, **Secondary Alarms**, **PSU 1 Fault** and **PSU 2 Fault**.

A **Command Response Message** parameter is also available, indicating whether a command was successfully executed or if an error occurred.

### Switches Page

The Switches page allows users to manage the position of switches using toggle buttons for Switches 1-8.

### Converters Page

The Converters page presents a table showing the current status of each converter. The table includes the following details:

- **Converter Instance**
- **Frequency**
- **Attenuation**
- **Second Attenuation**
- **Interface Bandwidth**
- **Fitted**
- **Mode**
- **Mute**
- **Inverted Spectrum**
- **Auto C/O Logic**
- **Input Fault**
- **Delayed Fault**
- **Communications Fault**
