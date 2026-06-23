---
uid: Connector_help_Digidia_EasyWay_Technical
---

# Digidia EasyWay

## About

The Digidia EasyWay is an IP-to-ETI gateway for DAB/DMB broadcasting networks. It receives an ETI-over-IP stream (EDI or Digidia proprietary protocol) and produces a synchronized ETI output for DAB/DMB modulators, using GPS- or NTP-based timing for SFN/MFN operation.

This connector uses SNMP to monitor and configure the gateway, and processes SNMP traps to report alarm notifications.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: Not required.

SNMP Settings:

- **Port number**: The IP port of the device (default: *161*).
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

Once the element has been created, the device data is organized across dedicated pages such as General, Version, System, Session, Ethernet, SNMP Settings, Traps, Log, Alarm, Options, Device Settings, GPS, Resend, and Relay.

SNMP polling is used to retrieve the device information shown on these pages. Configuration parameters (e.g. IP input settings, synchronization mode, NTP servers, and SNMP trap targets) can be written back to the device over SNMP using the writable parameters on the corresponding pages.

Alarm notifications are received as SNMP traps. To receive them, enable trap generation on the device and configure the DataMiner system as a trap target on the **SNMP Settings** page (trap target address and enable). Incoming traps update the Trap Alarm Notification table on the **Traps** page.

The device event log is retrieved on the **Log** page. The raw log time is converted to a human-readable value based on the current locale, and a table lists the logged events. The log can be cleared from the same page.

### Polling Manager

The **Polling Settings** page contains a Polling Manager table that lets you control how often each data set is polled:

- Use the **Interval** column to set a custom polling period per data set.
- Use the **Admin Status** column, or the table context menu, to enable or disable polling per row.
- Use the **Poll** button to poll a row immediately, or **Refresh All** to refresh every parameter.

## Notes

The connector provides a web page that links to the device web interface at `http://[Polling IP]/`.