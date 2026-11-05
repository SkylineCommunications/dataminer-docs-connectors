---
uid: Connector_help_Deep_Sea_Electronics_DSE8620_MkII_Technical
---

# Deep Sea Electronics DSE8620 MkII

## About

The **Deep Sea Electronics DSE8620 MkII** is a control unit designed for generator electrical panels.

## Configuration

### Connections

#### Serial Main Connection

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: *502*
  - **Bus address**: *1*

## How to use

The element created with this connector consists of the data pages detailed below.

## General

On this page, you can **upload** the following **CSV files**:

- **Modbus List**: File with the register address, description, multiplier, and units of the parameters. This file must be created manually based on information from the manual.
- Three files that can be exported from the device, containing the address and description of the parameters.

### Modbus Data Table

This page displays information about the Modbus CSV file.

### Data

On this page, you can view information from the device according to the parameters uploaded from the CSV file.
