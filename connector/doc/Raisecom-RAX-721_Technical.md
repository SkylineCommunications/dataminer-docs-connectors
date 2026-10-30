---
uid: Connector_help_Raisecom-RAX-721_Technical
description: "Configure SNMP polling and traps for Raisecom RAX 721, inspect device and interface health, and use interface controls safely in DataMiner."
---

# Raisecom-RAX-721 Technical

## About

The **Raisecom-RAX-721** connector monitors Raisecom RAX 721 system health, interface traffic, optical measurements, power supplies, and fans through SNMPv2. It also exposes selected device settings as SNMP write controls.

The connector requires **DataMiner 10.4.0.0 - 14003** or higher. No specific firmware version has been validated for this connector. Support for other RAX or ISCOM models is not established.

The deployed protocol name is **Raisecom RAX 721**. The Catalog title is **Raisecom-RAX-721**.

## Configuration

### Connections

#### SNMP Connection - Main

Configure the following settings when you create the element:

- **IP address/host**: The management IP address of the Raisecom RAX 721.
- **Port number**: The device's SNMP polling port, usually *161*. The connector does not override this standard port.
- **Get community string**: The read community string configured on the device.
- **Set community string**: A community string with device-side write permissions, if you intend to use SNMP controls.

#### SNMP Connection - Traps

The connector defines an additional **SNMP Connection - Traps** connection with port *162*. Configure the applicable device address in the element connection settings and configure the device to send its traps to the DataMiner Agent. Ensure that your network permits delivery to the configured trap receiver.

The implemented event handler processes Ethernet OAM event notifications with trap OID `1.3.6.1.2.1.158.0.2`. It maps the event to an interface and updates **Threshold Crossing Event** in the **Interfaces** table. This is not a general-purpose trap log.

### Initialization

When you have created the element:

1. Go to the **General** page and confirm that **Polling IP Address** identifies the intended management address and that **System Uptime** updates.
1. Go to the **Interfaces** page and confirm that the device interfaces are shown.
1. Review the **Power Devices** and **Fans** pages for the hardware reported by the device.
1. If event monitoring is required, configure device-side trap forwarding and check the per-interface **Threshold Crossing Event** values.

## How to Use

### Polling Behavior

The connector defines three initial polling schedules:

- **30 seconds**: System uptime.
- **3 minutes**: Interface and Ethernet statistics, optical diagnostics, CPU and memory measurements, device temperature, power supplies, and fans.
- **1 hour**: System name, contact, location, and description.

The timers are configured to run at element startup. Rate measurements require successive successful counter samples and might not be available immediately after startup.

There are no connector-specific controls on the data pages to set the polling interval or enable or disable datasets. **Rates Calculation Method for Interfaces Tables** changes rate calculation, not the polling interval.

### General Page

This page displays the following general information about the device:

- **System Uptime**, **System Name**, **System Contact**, **System Location**, and **System Description**.
- **Polling IP Address**, captured from the main connection at element startup.
- **CPU Utilization**, **Memory Total**, **Memory Available**, **Memory Utilization**, and **Temperature**.
- **Shutdown Reason**, which initially displays *None*. Do not treat this parameter as a complete shutdown event history. For incoming Ethernet OAM event information, use **Threshold Crossing Event** on the **Interfaces** page, which is updated based on traps.

You can edit the **System Name**, **System Contact**, and **System Location** parameters. These controls change the device, not only the DataMiner display.

### Interfaces Page

The **Interfaces** table combines the device's interface and extended-interface statistics into one row per interface. It shows interface descriptions, aliases, custom descriptions, administrative and operational status, type, MTU, speed, duplex status, promiscuous mode, and last-change and counter-discontinuity information.

Use **RX Bit Rate**, **TX Bit Rate**, and the corresponding bandwidth utilization values to assess traffic load. **RX Octets** and **TX Octets** provide cumulative counters.

#### Interface Labels

- **Alias** changes the interface alias on the device and requires SNMP write permissions.
- **Custom Description** sets a DataMiner-side label independently of the device.
- **Interfaces - Display Key Format** applies to the interface overview and both detail tables. Choose *Index : Description - Alias - Custom Description* or the default *Alias - Custom Description : Description*.

#### Rate Calculation

**Rates Calculation Method for Interfaces Tables** can be set to:

- *Fast* (default): Uses elapsed time at group level, with lower resource usage.
- *Accurate*: Uses elapsed time at table-row level, with higher resource usage and improved accuracy in some circumstances.

This setting applies to the underlying interface and extended-interface rate calculations.

#### Optical Measurements and Events

For interfaces with reported optical diagnostics, inspect **TX Power**, **RX Power**, **TX Bias Current**, **Transceiver Temperature**, and **Laser Temperature**. The table also includes **TX Power Status**, **RX Power Status**, and **Laser Temperature Status**. Missing optical measurements are shown as *N/A*, not as a zero reading.

**Threshold Crossing Event** displays the received supported event value: *Errored Framed Seconds*, *Link Fault*, *Dying Gasp*, or *Critical Link*. Trap delivery and the device's event reporting determine whether this column is populated.

#### Device Controls

You can set **Admin Status** to *Up*, *Down*, or *Testing*, and set **Promiscuous Mode** to *Enabled* or *Disabled*. These controls issue SNMP writes to the selected device interface.

> [!CAUTION]
> Changing **Admin Status** can interrupt traffic or remove the management path to the device. Changing **Promiscuous Mode** changes which packets the interface accepts. Assess the affected interface and service impact before applying either control.

**Last Clear** is counter-discontinuity information, not a button to clear counters.

### Interfaces Details Page

The **Interfaces Details** page contains two tables linked to the corresponding **Interfaces** rows:

- **Interfaces Details RX**: Receive unicast, broadcast, multicast, discard, error, and unknown-protocol rates.
- **Interfaces Details TX**: Transmit unicast, broadcast, multicast, discard, and error rates.

Use the shared display keys to compare the same interface across the overview and both detail tables. These tables show rates rather than a packet capture.

### Power Devices Page

The **Power Devices** table shows each reported power supply's SNMP instance and index, presence ("Exist"), input type, input availability ("Input"), and warning type. Warning values include *Unknown*, *Voltage Over*, *Power Normal*, *Voltage Under*, and *Power Down*.

Use this page to distinguish a missing supply or missing input from a supply warning. The displayed table is read-only and does not provide a power reset control.

### Fans Page

The **Fans** table shows each reported fan's SNMP instance and index, presence ("Exist"), status, and speed. Status values distinguish *Normal* from *Abnormal*. The table is read-only.
