---
uid: Connector_help_Digidia_SpanFM2_Technical
description: Learn how to monitor and configure the Digidia SpanFM2 multiplexer via SNMP in DataMiner, including alarm tables, polling options, and web control.
---

# Digidia SpanFM2

## About

The Digidia SpanFM2 connector monitors and controls a Digidia SpanFM2 audio multiplexer over SNMP. The SpanFM2 is a broadcast headend device used to assemble, process, and synchronize audio services for DAB/DAB+ and FM radio distribution. The connector exposes the device status, alarms, version and inventory information, and configuration of the network, time synchronization, SNMP trap targets, and user access.

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

The **Website** page opens the device web interface at `http://[Polling IP]/`, where `Polling IP` is the IP address configured for the SNMP connection.

## How to Use

SNMP polling is used to retrieve all device information. Values are read on the General, Alarm, Multiplex, Version, System, Session, Communication, Trap, Logs, and Synchronisation pages. Writable parameters use SNMP set requests, which require a correctly configured Set community string.

### Monitoring

- **Multiplex** page: Shows the multiplex audio service status, including the system, synchronization, audio input, data mailbox input, wave file input, PIMS over RS-232 input, redundancy, and UECP input states. Each state is monitored and raises a DataMiner alarm when active. The multiplex alarm notification table and the multiplex redundancy status are also displayed here.

- **Alarm** page: Shows the global alarm table reported by the device, including the description, type, status, and additional info for each alarm.

  Each alarm can be given a **custom description**, which must be unique. If a value is already used by another alarm, either as its custom description or as its *Description/Info*, it is rejected with a pop-up message. Custom descriptions are kept when the **Global Alarm Table** polling is disabled in the Polling Manager.

  The **Global Alarm Display Key Format** parameter selects whether alarms are identified by *Description/Info* (default) or by their *Custom Description*. Alarms without a custom description fall back to *Description/Info*.

- **Version** page: Reports the MIB, software, hardware, and code software versions.

- **Logs** page: Shows the device event log (Elog) entries. The raw hexadecimal time values reported by the device are converted to a readable date/time.

### Configuration and Control

- **System** page: Allows you to set the equipment name, comment, real-time clock, serial number, and license keys, and trigger an equipment reset.

- **Communication** page: Allows you to review and set the network configuration of both Ethernet interfaces (IP address, subnet mask, gateway, and port speed/duplex).

- **Synchronisation** page: Allows you to configure the two NTP server addresses used by the device.

- **Session** page: Allows you to configure public access and manage the user table (name, password, and access level).

- **Trap** page: Allows you to configure the SNMP trap community and enable up to two trap targets, including the IP address of each manager that should receive traps from the device.

### Polling Settings

On the **Polling Settings** page, the **Multiplex Audio Service Type** row in the **Polling Manager** controls polling for PIDs 500-507 and **FM Default Indication by PIMS to Spanfm2** (PID 800). These share the same configurable polling interval (default: *30 seconds*), enable/disable state, and manual poll controls. Disabling this row resets PID 800 and PIDs 500-507 to `-1`. There is no separate FM polling row.

## Notes

- The connector monitors device redundancy through the multiplex redundancy status and the redundancy alarm. This reflects the SpanFM2 internal redundancy between paired multiplexers and does not require any DataMiner redundancy configuration.
- Several time and log values are reported by the device as hexadecimal strings; the connector converts these to readable values for display.
