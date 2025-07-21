---
uid: Connector_help_Paradise_RCP-1200_Technical
---

# Paradise RCP-1200

The **Paradise RCP-1200** protocol is used to monitor and control amplifiers configured in redundant systems.

## About

This protocol can be used to monitor and control any Paradise RCP-1200 device. A **TCP/IP** connection is used to retrieve and configure the settings of the device.

## Installation and configuration

### Creation

**Serial Connection:**

- **Type of port**: The type of port of the connection. By default: *TCP/IP*.
- **IP address/host**: The polling IP of the device. For instance: *10.1.48.70*.
- **IP port**: The IP port of the device. By default: *4012*.
- **Bus address**: The source address of the device, within the range of **0–31**. For instance: *06*.

## Usage

### Fault Status

The fault status information of the device:

- **Summary Fault**: Indicates whether a system-wide fault has occurred (amplifiers, processor, power supplies, RF switches).
- **PS**: Displays whether the power supply is *Faulted* or *Normal*.
- **RF Switch**: Displays whether the position of the switch is set to *POS1* or *POS2*.
- **Fault Monitoring**
- **(External) Amplifier Power**: Displays whether the external amplifier is *Faulted* or *Normal*.
- **External UID**: Displays the status of External User Defined Inputs (e.g., *Normal* or *Fault*).

### System Setup

The control settings of the device:

- **Panel/Remote Mode**
- **Auto/Manual Mode**
- **Amplifier Standby**
- **Priority**
- **Buzzer**
- **Communication**: Displays the **Unit Address**, **Serial Baud Rate**, **Communication Protocol**, **Unit Hierarchy**, and **System Redundancy**.
