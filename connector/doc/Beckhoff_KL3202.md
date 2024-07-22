---
uid: Connector_help_Beckhoff_KL3202
---

# Beckhoff KL3202

The **Beckhoff KL3202** is a serial connector that is used to monitor two resistance temperature detectors.

## About

This connector allows the user to read the status of two resistance temperature detectors. To be able to read values, the Beckhoff KL3202 element needs a **virtual** connection with a **Beckhoff BK9000** element.

## Installation and configuration

### Creation

This connector uses a serial connection and requires the following input during element creation:

**SERIAL CONNECTION:**

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13.*
- **IP port**: The port of the connected device, e.g. *4001.*
- **Bus address**: The bus address set in the device, e.g. *1*. (range: *1* to *9999.*)

### Configuration

The **PositionInfo from BK9000** needs to be configured with a virtual connection to the **PositionInfo** of the right entry of the **Module Table** in the **Beckhoff BK9000** connector. This connection is needed because the Beckhoff BK9000 provides the Beckhoff KL3202 element with a start and stop position. These are used in the serial communication to set the relays.

## Usage

### General

This page displays the values of two resistance temperature detectors.
