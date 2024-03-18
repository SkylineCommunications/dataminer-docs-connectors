---
uid: Connector_help_Suitelife_Systems_GPX-32
---

# Suitelife Systems GPX-32

The Suitelife Systems GPX-32 connector has been designed to monitor and manage the Suitelife Systems GPX-32 IO Contact Interface

## About


### Version Info

| **Range** | **Description**                 | **DCF Integration** | **Cassandra Compliant** |
|------------------|---------------------------------|---------------------|-------------------------|
| 1.0.0.x          | Initial Version - Serial RS-232 | No                  | Yes                      |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | -                           |

## Installation and configuration

### Creation

This connector uses a serial single connection and requires the following input during element creation:

 Interface connection:

  - **IP address/host**: The polling IP of the device.
  - **IP port**: The IP port of the device.
  - **Bus address**: The bus address of the device. *This must match the MODBUS address of the device.*

## Usage

### General

General page, displays the Analog Voltage Range table.

### Status

This page displays the Status table

### Analog

This page displays the Analog table

### Control

This page displays the Control table