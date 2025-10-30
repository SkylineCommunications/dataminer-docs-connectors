---
uid: Connector_help_Vertex_RSC-1200
---

# Vertex RSC-1200

## About

This connector allows you to monitor the **Vertex RSC-1200** SWO device.

### Product Info

| Range | Supported Firmware |
|--|--|
| 1.0.0.x | 3.00<br>2.12 |

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:
  
  - **Baudrate**: Baudrate specified in the manual of the device.
  - **Databits**: Databits specified in the manual of the device. (default: 8)
  - **Stopbits**: Stopbits specified in the manual of the device. (default: 1)
  - **Parity**: Parity specified in the manual of the device. (default: no)
  - **FlowControl**: FlowControl specified in the manual of the device.

- Interface connection:

  - **Type of port**: TCP/IP
  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus:** the bus address, in case of any (Range: 0 - 255)

## How o Use

### General Page

This page contains general information about the device such as **Power Supply** and **Unit Current**. Here you can also find page buttons to the **Controller Alarms**, **Switch Control** and the **Event Log**.

### Configuration Page

This page displays configurable parameters such as **Redundancy Mode**, **Remote Control**, **Noise Diode**, etc.

### Internal/External Input Alarms Page

This page displays the **Alarm Statuses** of the device.
