---
uid: Connector_help_Evertz_MUXIP-10GE-v52-2RU
---

# Evertz MUXIP-10GE-v52-2RU

## About

The **Evertz MUXIP-10GE-v52-2RU** is a versatile IP re-/de-multiplexer designed for video delivery. It supports up to 128 IP inputs and outputs, handles both SPTS and MPTS, and offers advanced stream processing features like program and PID remapping. With robust redundancy options and flexible configuration, it is ideal for broadcasters and service providers managing high-quality video content across networks.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to use

Once the element is created, all information will be polled and displayed. Navigating to the appropriate pages will show the desired information, no other configuration is required.

### Examples

You can find general device information on the **General**, **Status**, **System Configuration**, and **Ethernet Ports Control/Monitor** pages.

The device can forward any faults via SNMP traps. To activate this, enable the **Send Trap** option for the relevant modules on the **Fault** page, and then configure where to send the traps on the **SNMP Configuration** page.

To configure the input and output channels, you can find all relevant information on the **Input Configuration** and **Output Configuration** pages, respectively. To configure route rules, go to the **Routes** page.
