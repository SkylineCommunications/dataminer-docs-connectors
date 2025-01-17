---
uid: Connector_help_Double_D_Electronics_DDA219-511E
---

# Double D Electronics DDA219-511E

This connector monitors the activity of the **Double D Electronics DDA219-511E** switch controller.

The connector uses serial communication to allow the end user to control and monitor the switch configuration.

## About

### Version Info

| Range              | Key Features    | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | V1.28T13           |

### System Info

| Range              | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--------------------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x            | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:

  - **Baudrate**: Baudrate specified in the manual of the device, e.g. *9600* (range: *1200* - *115200*).
  - **Databits**: Databits specified in the manual of the device, e.g. *7* (default: *7*).
  - **Stopbits**: Stopbits specified in the manual of the device, e.g. *1* (default: *1*).
  - **Parity**: Parity specified in the manual of the device, e.g. *No* (default: *Even*).
  - **FlowControl**: FlowControl specified in the manual of the device, e.g. *No* (default: *No*).

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination.
  - **Bus address**: The bus address of the device.

## How to use

On the General page, on the left, you can view general information about the device, such as the **Software Version**, the **Device Name**, the **Maximum Number of Supported Switches**, and the **Maximum Number of Supported Chains**.

You can also define the mode of the device (using the **Global Device Mode** parameter) and its respective **Control Mode**.

On the right, the page shows if there are any **Active Alarms**, **Unacknowledged Alarms**, or **PSU 1** and **PSU 2 Alarms**.
