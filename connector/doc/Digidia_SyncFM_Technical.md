---
uid: Connector_help_Digidia_SyncFM2_Technical
description: Learn how to configure and operate the Digidia SyncFM SNMP connector for SyncFM2 and SyncFM4, including polling and traps.
---

# Digidia SyncFM

## About

The Digidia SyncFM connector monitors and controls Digidia SyncFM devices over SNMP, including SyncFM2 and SyncFM4 audio processors. These devices provide GPS-locked synchronization for FM broadcast networks, distributing time-aligned audio and user-channel (RDS) data to transmitter sites so a Single Frequency Network (SFN) can operate without interference in overlap zones.

The connector polls the device for GPS reception, synchronization, IP audio input, user-channel, system, and alarm information, and processes SNMP traps sent by the device for real-time alarm notifications.

## Configuration

### Connections

#### SNMP Connection - Digidia SyncFM

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: Polling IP address or host name of the Digidia SyncFM device.
- **Device address**: Not required.

SNMP Settings:

- **Port number**: Port of the connected device, by default 161.
- **Get community string**: Community string used when reading values from the device (default: public).
- **Set community string**: Community string used when setting values on the device (default: private).

The device also sends SNMP traps that this connector processes for alarm notifications. To receive them, the device must be configured to send traps to the DataMiner Agent (see [Initialization](#initialization) below).

### Initialization

After you create an element, verify the following:

- The SNMP community strings and polling port match the device configuration.
- On the **Polling Settings** page, review and, if needed, enable or adjust polling. The connector includes a Polling Manager that lets you enable, disable, and schedule polling of individual parameter groups (System Information, Alarm Status, Device Settings, GPS, User Channel, External IOs, and others).
- On the **Trap** page, review SNMP trap settings so the device is configured to send trap notifications to the DataMiner Agent. This is required for real-time alarm notifications.

### Web Interface

The device exposes a web interface, accessible from the **Website** page of the element (`http://[Polling IP]/`).

The web interface is only accessible when your client machine has network access to the device.

## How to Use

Once the element is created and polling is active, the connector organizes device information across the following pages:

- **General** / **Version** / **System**: General system information (system description, object ID, uptime, contact, name, location), MIB and firmware version details, and system data such as equipment name, type, serial number, real-time clock (RTC), last error, and equipment state. The **System** page also provides the **Reset Equipment** command.

- **Synchronisation** / **Device Settings**: Core synchronization parameters, including **Synchronisation Mode** (MFN / SFN), synchronization alarm status, system clock lock state, and **Output Auxiliary Clock Frequency**.

- **GPS**: GPS reference monitoring, including **GPS Status** (Locked/Unlocked), number of visible satellites, average satellite SNR, leap seconds, cable delay, and decoded geographic position. The human-readable **GPS Position** is derived by the connector from the raw octet string reported by the device.

- **User Channel**: User-channel (audio/RDS distribution) configuration such as site and start address, database version, AES output state, breaking order, studio number, current active group, main program SCID and mode, main breaking program SCID and mode, transmitter time delay, and group number, together with the User Channel Group table.

- **Alarm**: Aggregated alarm status for IP input, synchronization, control process, and system, plus granular alarms such as IP input underflow/overflow, uncorrected IP input packets, system clock unlock, SFN error, GPS receiver unlocked, empty user-channel database, missing user-channel sub-stream, missing sub-channel to decode, and system hardware/software faults. The Sync Alarm Notification table and the Alarms Bool Setting table are also available here.

- **External IOs**: State of external inputs and external relay command, together with the alarm relay status table.

- **Communication**: Network (Ethernet) configuration of the device.

- **Session**: Session User table, listing users connected to the device.

- **Trap**: SNMP trap settings and the most recent trap alarm notification. Traps received from the device are processed automatically and reflected in relevant alarm parameters.

- **Logs**: Event log (Elog) settings and the Elog table.

- **Polling Settings**: Polling Manager, where polling of each parameter group can be enabled, disabled, and scheduled.

Writable parameters (for example, synchronization mode, IP input settings, output auxiliary clock frequency, and external relay command) can be set directly from the corresponding pages when the device permits it.

## Notes

- The connector communicates with the device exclusively over SNMP. The **Website** page is a convenience link to the device web interface and is not part of SNMP data exchange.
- Real-time alarm notifications rely on SNMP traps. If the device is not configured to send traps to the DataMiner Agent, alarm information is still updated, but only at the polling interval configured in the Polling Manager.
- The **GPS Position** value shown on the GPS page is computed by the connector from the raw position octet string reported by the device.
