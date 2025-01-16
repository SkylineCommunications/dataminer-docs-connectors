---
uid: Connector_help_Double_D_Electronics_DDA219-511E
---

# Double D Electronics DDA219-511E

The connector monitors the activity of the **Double D Electronics DDA219-511E** switch controller.

## About

The connector has a serial communication to the **Double D Electronics DDA219-511E** and allows the end user to control and monitor the switch configuration.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|------------------|-----------------|---------------------|-------------------------|
| 1.0.0.x [SLC Main]          | Initial version | No                  | Yes                     |         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |V1.28T13         |

## Configuration

### Connections

#### Serial Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:


- Direct connection:

  - **Baudrate**: [Baudrate specified in the manual of the device, e.g. *9600*. (range: *1200* - *115200*)]
  - **Databits**: [Databits specified in the manual of the device, e.g. *7*. (default: *7*)]
  - **Stopbits**: [Stopbits specified in the manual of the device, e.g. *1*. (default: *1*)]
  - **Parity**: [Parity specified in the manual of the device, e.g. *No*. (default: *Even*)]
  - **FlowControl**: [FlowControl specified in the manual of the device, e.g. *No*. (default: *No*)]


- Interface connection:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination.]
  - **Bus address**: [The bus address of the device.]

## How to use

On the general page, the user can observe some general information from the device on the left such as the **Software Version;** the **Device** **Name**; the **Maximum** **Number of Supported Switches** and the **Maximum Number of Supported Chains**.

In addition to the previous, the user can define the device's mode (**Global Device Mode**) and its respective **Control Mode**.

At the right of the page the user can observe if there's any existing alarms regarding: **Active Alarms; Unacknowledged Alarms; PSU 1** and **PSU 2 Alarm.**