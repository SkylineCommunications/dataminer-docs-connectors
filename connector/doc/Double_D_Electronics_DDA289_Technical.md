---
uid: Connector_help_Double_D_Electronics_DDA289_Technical
---

# Double D Electronics DDA289

## About

This connector can be used to monitor the activity of the Double D Electronics DDA289 redundancy controller.

The connector uses serial communication and allows the end user to switch positions and view the status of the device's converters.

Three polling intervals are used to gather data at different rates:

- Every 5 seconds: Captures rapidly changing information, such as switch positions and converter status information.
- Every 1 minute: Retrieves the summary status of the controller.
- Every 1 hour: Collects data that changes infrequently, such as controller configuration data.

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | DDA289 V0.11                |

## Configuration

### Connections

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

## How to Use

### General Page

On the left side of the General page, you can find key information about the device, including the **Unit Type**, **Software Version**, **Number of Supported Paths**, **Number of Switch Banks Fitted**, **Equipment Name**, and **Configuration Version**.

You can also set the **Global Device Mode** and its corresponding **Control Mode**.

On the right side of the page, you can see the status of any alarms or power supply issues, including **Primary Alarms**, **Secondary Alarms**, **PSU 1 Fault**, and **PSU 2 Fault**.

A **Command Response Message** parameter is also available, indicating whether a command was successfully executed or if an error occurred.

### Switches Page

The Switches page allows you to manage the position of switches using toggle buttons for switches 1-8.

### Converters Page

The Converters page displays a table with the current status of each converter. The table includes the following details:

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
