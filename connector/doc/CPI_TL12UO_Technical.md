---
uid: Connector_help_CPI_TL12UO_Technical
---
# CPI TL12UO

## About

This connector is intended to communicate with the device using serial commands as described in the device's manual. For more information, refer to <https://www.cpii.com/pe-amplifier-products/product/satcom-twtas-156/outdoor-twtas-ku-band-817>.

## Configuration

### Connections

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- **Type of port:** TCP/IP
- **IP address/host**: e.g. *10.11.12.13.*
- **IP port**: default: *50000*
- **Bus address**: default: *48*

## How to Use

### General

This page contains general information about the device.

Via the **Log** page button, you can get a log entry from the device, by setting the **Log Entry RF Units** and **Log Entry Number to Get** parameters. Retrieving the same entry number with a different unit will overwrite the row with the same entry number.

### Measurements

Several measurement points of the device are shown here.

### Switch Controller

This page contains parameters that control the switch's position and priority.

### Switch System Status

This page shows the status of the switch.

### Settings

On this page you can set the **name** of the amplifier as well as set the time of the device using the **Set Time** page button. Switch-related settings are also available here.

### Alarms

All alarms related to the device are shown here. Via the page buttons, you can get the alarms related to each component of the device.

### Web Interface

This page can be used to access the web interface of the device.
