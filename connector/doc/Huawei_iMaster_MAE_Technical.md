---
uid: Connector_help_Huawei_iMaster_MAE_Technical
---

# Huawei iMaster MAE

## About

The Huawei iMaster MAE connector integrates the Huawei iMaster MAE-Access management system into DataMiner. It processes SNMPv3 alarm and heartbeat traps forwarded by the iMaster MAE northbound interface and synchronizes a daily network element (NE) inventory retrieved over SFTP.

Alarm traps are stored in an Alarms Overview table, heartbeat traps drive a device availability watchdog, and the inventory export is parsed and loaded into a dedicated Inventory table.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses an SNMPv3 connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the Huawei iMaster MAE-Access node.
- **Device address**: The device address of the node.

SNMP Settings:

- **IP port**: The IP port used for the SNMP connection.
- **Security settings**: The SNMPv3 credentials (username, authentication, and privacy settings) as configured on the iMaster MAE northbound interface.

### Initialization

After you have created the element, configure the following settings on the *Configuration* page before you start using the connector:

- **SFTP Host**: The hostname or IP address of the SFTP server hosting the daily inventory CSV export.
- **SFTP Username** and **SFTP Password**: The credentials used to authenticate to the SFTP server.
- **SFTP Remote Directory**: The remote directory containing the daily inventory CSV export, for example, `/opt/oss/server/var/fileint/cm/Report/`.
- **Heartbeat Timeout**: The number of seconds without a heartbeat trap after which the device is considered *Unavailable* (default: 180s).

Until you configure the SFTP settings, the inventory table is not populated, and the *Last Inventory Result* parameter indicates that the connector is not yet configured.

To monitor alarm states, assign an alarm template to the monitored parameters, for example *Device Availability* and the alarm trap severity. The alarm template determines the severity assigned to these parameters.

## How to Use

The connector is trap-driven. No active polling of the device takes place for alarms and heartbeats. Alarm and heartbeat traps must be forwarded from the iMaster MAE northbound interface to the DataMiner Agent. Because these traps are not actively polled, no request/response traffic is visible in the Stream Viewer for the trap flows.

### General Page

Displays high-level statistics, including the number of active alarms and the inventory row count.

### Inventory Page

Displays the network element inventory loaded from the daily CSV export, keyed on NE Name. Each refresh upserts the rows found in the file and removes rows for NEs no longer present.

### Alarms Page

Displays the Alarms Overview table populated with received alarm traps, including severity (Alarm State), alarm status (Active or Cleared), and timestamps.

### Configuration Page

Contains the device status parameters (last heartbeat received, time since last trap, device availability, heartbeat timeout), the SNMP trap section, the SFTP configuration, and the inventory status.

- **Force Update Inventory**: Triggers an immediate download and refresh of the inventory CSV, bypassing the once-per-day guard applied during automatic hourly polling.

## Notes

- Inventory refreshes are limited to once per day. The automatic hourly poll continues retrying until the file for the current day has been loaded.
- The Alarms Overview table currently contains only trap-sourced alarms and is cleared when the element is restarted.
