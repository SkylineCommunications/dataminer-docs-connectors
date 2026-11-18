---
uid: Connector_help_Electrolink_FM_Transmitter_Technical
description: "Monitor and configure an Electrolink FM transmitter with DataMiner over SNMPv2, including power, status, network settings, traps, and email configuration."
---

# Electrolink FM Transmitter

## About

The **Electrolink FM Transmitter** connector monitors and manages the transmitter over SNMPv2. It provides operational measurements, status monitoring, and controls for transmitter configuration.

The connector requires DataMiner 10.4.0.0 build 14003 or later.

## Configuration

### Connections

#### SNMP Connection

This connector uses an SNMPv2 connection. During element creation, configure the transmitter's polling IP.

- **IP address/host**: The polling IP of the transmitter
- **IP port**: The IP port of the transmitter (default: *161*)
- **Bus address**: Not required

## Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General Page

On this page, you can review the transmitter system name and version, real-time clock (RTC) status, and RTC date and time. The RTC date and time can be edited.

Note that the editable system location is shown on the **Mail** page instead.

### LAN Page

On this page, you can view the transmitter MAC address and configure its IP address, subnet mask, gateway, and primary and secondary DNS addresses.

> [!CAUTION]
> Changing the transmitter IP address interrupts communication with DataMiner until the element is updated to use the new address.

### SNMP Page

On this page, you can enable or disable trap sending, set the trap destination address, and review the status of the last trap sent by the transmitter.

### Mail Page

On this page, you can enable or disable email sending and configure the SMTP server and port, username, sender address, and up to two recipient addresses. The system location can also be viewed and edited here.

The page also shows the last sending result, maximum and sent email counts, and the sending window.

The SMTP password is an editable protected setting; it is not available as a readback value.

### System TX Page

On this page, you can view the overall transmitter status, forward and reflected power, heat sink temperature, driver forward power, and supply voltage and current, as well as the fan, interlock, VSWR, temperature, and RF output status.

This page also shows the VSWR block state and enabled or disabled state of the transmitter.

You can set the output power level, enable or disable the transmitter, and use **Reset VSWR Block**.

Alarm suitability and thresholds for analog measurements depend on the transmitter configuration or site wiring.

### Polling Settings Page

Use the **Polling Manager** table to configure each dataset's polling interval and enabled state, review its last polling time and result, or poll a row immediately.

The context menu of the table provides row and bulk operations, including enabling, disabling, polling, and resetting intervals to their defaults. The **Refresh All** option immediately polls all enabled datasets.

Disabling a dataset clears its parameters. The connector uses dynamic Polling Manager intervals; configure them **per dataset** for the deployment.

## Web Interface Page

The **Web Interface** page will open the transmitter's web interface using the configured polling IP.
