---
uid: Connector_help_ETL_Systems_23222_-_23223_Technical
---

# ETL Systems 23222 - 23223

## About

ETL Systems 23222 unit is a 32:1 switch with 32 inputs and 1 output and 1 RF monitoring port.
This communicationn protocol allows for full control and monitoring of the system.

## Configuration

### Connections

#### IP connection

The connector uses IP connection to connect to the monitored device. That means that the user will need to enter the correct IP address and port when creating the element for the first time.

## How to use

### General page

The general page contains the **Basic Control and Status** section and the **Chassis Status** section.

There are statuses for *PSU 1* and *PSU 2* for the matrix as well as for the Chassis.

Parameter *Matrix Status* indicates the alarm summary of the matrix. It can be *Ok* or *Failed*.

Button *Short Switch* allows the user to switch the selected multi-port to the common-port.

User also has the option to change the address of the chassis with the *Chassis Status Address*.

### Monitoring page

Monitoring page provides real-time status tracking for key system parameters. It is divided into three key sections:

- *Temperature monitoring*: Tracks the CPU temperature.
- *Voltage monitoring*: Tracks the *PSU 1* and *PSU 2* voltages as well as *PSU Bus voltage* and *5V and 3V Rail* voltages.
- *Current monitoring*: Tracks the *Amplifiers 1,2 and 3 Bias Currents*.

Also on the page user can retrieve the *Monitoring Status* and can change the limits to the ±20% upper and lower limits for the Amplifier bias currents on the specified chassis.

### Configuration page

Configuration page contains numerous parameters that user change based on their preference.

User can change the shelf name and can retrieve all of the aliases change their address and reset them to their default values. Number of matrix multi and common-ports can be edited. Base and Chassis IP can also be changed. Dataport port and timeout can be edited as well.

This page contains also information *Firmware* and *Bootloader*. It contains informations such as *revision*, *number* and *date* for both firmware and bootloader.