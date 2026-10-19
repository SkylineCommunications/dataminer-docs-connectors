---
uid: connector_Electrolink_FM_Transmitter_100W_Technical
---
# Electrolink FM Transmitter 100W

## About

The **Electrolink FM Transmitter 100W** connector monitors and manages the transmitter over SNMPv2. It provides operational measurements, status monitoring, and controls for transmitter configuration.

The connector requires DataMiner 10.4.0.0 build 14003 or later.

## Configuration

### Connections

#### SNMP Connection

This connector uses an SNMPv2 connection. During element creation, configure the transmitter's polling IP.

| Setting | Value |
|---------|-------|
| **IP address/host** | The polling IP of the transmitter |
| **IP port** | The IP port of the transmitter (default: *161*) |
| **Bus address** | Not required |

## How to Use

### General

Review the transmitter system name and version, real-time clock (RTC) status, and RTC date and time. The RTC date and time can be edited. In the current protocol layout, the editable system location is shown on the **Mail** page.

### LAN

Review the transmitter MAC address and configure its IP address, subnet mask, gateway, and primary and secondary DNS addresses.

> [!WARNING]
> Changing the transmitter IP address interrupts communication with DataMiner until the element is updated to use the new address.

### SNMP

Enable or disable trap sending, set the trap destination address, and review the status of the last trap sent by the transmitter.

### Mail

Enable or disable email sending and configure the SMTP server and port, username, sender address, and up to two recipient addresses. The page also shows the last sending result, maximum and sent email counts, and the sending window. The SMTP password is an editable protected setting; it is not available as a readback value. The current protocol layout also places the editable system location on this page.

### System TX

Review overall transmitter status; forward and reflected power; heatsink temperature; driver forward power; supply voltage and current; and fan, interlock, VSWR, temperature, and RF output status. This page also shows the VSWR block state and transmitter enabled or disabled state. Operators can set the output power level, enable or disable the transmitter, and use **Reset VSWR Block**.

Alarm suitability and thresholds for analog measurements depend on the transmitter configuration or site wiring. The connector documentation does not define universal limit values.

### Polling Settings

Use the Polling Manager table to configure each dataset's polling interval and enabled state, review its last poll time and result, or poll a row immediately. The context menu provides row and bulk operations, including enabling, disabling, polling, and resetting intervals to their defaults. **Refresh All** immediately polls all enabled datasets. Disabling a dataset clears its parameters. Polling intervals are configurable per dataset and are not a single fixed connector interval.

## Web Interface

The **Webinterface** entry opens the transmitter's web interface using the configured polling IP.

The web interface is only accessible when the client machine has network access to the product.

## Notes

- The connector uses dynamic Polling Manager intervals; configure them per dataset for the deployment.
- Firmware compatibility is not specified in the available protocol and MIB sources.