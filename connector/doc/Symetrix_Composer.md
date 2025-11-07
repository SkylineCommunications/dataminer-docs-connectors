---
uid: Connector_help_Symetrix_Composer
---

# Symetrix Composer

## About

The Symetrix Composer is a Windowsr application used to program Radius, Prism, Edge, and Solus NX DSPs.

This connector uses two connection a Serial and HTTP connection to poll data from the Symetrix Composer. The serial connection is responsible for the polling of the controllers' value and the HTTP is responsible for the polling

of the system information.

## Configuration

### Connections

#### Serial Connection - Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Direct connection:
  - **Baudrate**: Baudrate specified in the manual of the device.
  - **Databits**: Databits specified in the manual of the device.
  - **Stopbits**: Stopbits specified in the manual of the device.
  - **Parity**: Parity specified in the manual of the device.
  - **FlowControl**: FlowControl specified in the manual of the device.
- Interface connection:
  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.

#### HTTP Connection - Secondary

This connector uses a HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device.

## How to Use

### General

This page contains general information about the device such as, **Name, Fan Speed, Board Temp and Main DC**.

This page also contains two system commands:

- **Flash LEDs**: Allows you to flash LEDs on the main console based on how much cycles are selected.
- **Load Preset**: Allows you to load a preset to the device.

### Controller

This page contains the **Controller Table**. You can add controllers to this table one by one or in bulk using a CSV file. In the table, you can also adjust settings for the different type of controllers available. Note that information entered in the dropdown list column in the table must be entered in **Controller Number/Option** format.

### Best Practice

This page contains information on how to use the connector.

### Web Interface

This page displays the web interface of the device.

Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
