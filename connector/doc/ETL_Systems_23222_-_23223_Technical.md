---
uid: Connector_help_ETL_Systems_23222_-_23223_Technical
---

# ETL Systems 23222 - 23223

## About

The ETL Systems 23222 unit is a 32:1 switch with 32 inputs, 1 output, and 1 RF monitoring port. This connector allows full control and monitoring of the system.

## Configuration

### Connections

#### IP connection - Main

This connector uses an IP connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the destination.
- **IP port**: The IP port of the destination.

## How to use

### General page

The General page contains the **Basic Control and Status** section and the **Chassis Status** section, with status information for PSU 1 and 2 for the matrix as well as the chassis.

The **Matrix Status** parameter indicates the alarm summary of the matrix (*Ok* or *Failed*).

With the **Short Switch** button, you can switch the selected multi-port to the common port.

You can also change the address of the chassis with the **Chassis Status Address** parameter.

### Monitoring page

The Monitoring page provides real-time status tracking for key system parameters. It is divided into three key sections:

- **Temperature monitoring**: Tracks the CPU temperature.
- **Voltage monitoring**: Tracks the PSU 1 and PSU 2 voltages as well as the **PSU Bus** voltage and **5V and 3V Rail** voltages.
- **Current monitoring**: Tracks the amplifiers 1, 2, and 3 bias currents.

You can also retrieve the monitoring status on this page, and you can change the limits to the ±20% upper and lower limits for the amplifier bias currents on the specified chassis.

### Configuration page

On this page, you can change numerous parameters based on your preferences: You can change the shelf name, retrieve all of the aliases, change their address, and reset them to their default values. You can also edit the number of matrix multi-ports and common ports, the base and chassis IP, and the data port and timeout.

The page also contains information about both the firmware and bootloader: the revision, number, and date.
