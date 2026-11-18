---
uid: Connector_help_Radeus_Labs_ACU_8200_Technical
description: "Learn how to connect to the Radeus Labs ACU 8200 over SNMP, monitor antenna and receiver data, and configure device settings."
---

# Radeus Labs ACU 8200

## About

The 8200 ACU is compatible with industry-standard drive cabinet interfaces and legacy position feedback devices such as absolute rotary optical encoders, standard single-speed brushless size-11 resolvers, and two-speed brushless size-20 resolvers.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a SNMP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## How to Use

The element created with this connector consists of the data pages described below. Each page displays information about the **Actual Positions** of the antenna and **Receiver** parameters like the **Receiver Signal Level**.

### General

This page displays general system parameters such as **System Name**, **System Location**, and the **Database Version**.

### Main View

This page contains **Status** information about the device.

### Settings

On this page, you can configure the device settings. More information is displayed on each subpage: **Site**, **Receiver**, **Encoders**, **Limits**, **Motion**, **Timing**, **Options**, **Positioner**, and **Targets**.
