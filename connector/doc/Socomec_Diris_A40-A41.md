---
uid: Connector_help_Socomec_Diris_A40-A41
---

# Socomec Diris A40-A41

## About

The Socomec Diris A40-A41 is a multi-meter for electric values in single-phase, two-phase, and three-phase LV and HV networks. This connector monitors the device using serial communication. The commands are sent to an Ethernet module that is directly attached to the device.

## Configuration

### Connections

This connector uses a serial connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the device, e.g., *10.11.12.13*.
- **Device address**: The bus address (unit ID), in the range 1–247.
- **Port number**: The port of the connected device, by default *502.*

## How to Use

### General page

On the **General** page, there are different blocks of data:

- Current
- Power
- Power Consumption
- Phase To Neutral Voltage
- Phase to Phase Voltage
- Temperatures

Each of these blocks displays information about the parameters related to the block.

There are three page buttons on this page that each lead to a pop-up page with additional information. In addition, there is one button available, **Reset**, that will perform a reset.

### Webpage

This page displays the webpage associated with the device.
