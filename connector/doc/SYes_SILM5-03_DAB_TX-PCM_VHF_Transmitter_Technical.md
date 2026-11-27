---
uid: Connector_help_SYes_SILM5-03_DAB_TX-PCM_VHF_Transmitter_Technical
description: Configuration and usage of the SYes SILM5-03 DAB TX-PCM VHF Transmitter connector - SNMPv3 connection, pages, polling, and web interface.
---

# SYes SILM5-03 DAB TX-PCM VHF Transmitter

## About

The **SYes SILM5-03 DAB TX-PCM VHF Transmitter** connector monitors and manages the SYes SILM5-03 DAB transmitter via **SNMPv3**. It provides visibility into RF power output, exciter and amplifier health, input signal status, and transmitter alarms, and allows remote configuration of exciter and input switching behavior.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the transmitter.
- **IP port**: The IP port of the transmitter (default: *161*).
- **Bus address**: Not required.

As the connector uses SNMPv3, also configure:

- **Security level and protocol**: The SNMPv3 security level and protocol configured on the transmitter.
- **User name**: The SNMPv3 user name.
- **Authentication and privacy passwords**: As configured on the transmitter.

### Initialization

On element startup, the connector populates the **Web Interface** parameter on the **General** page with the polling IP of the transmitter. If the transmitter web interface is reachable on a different address, overwrite the **Web Interface** parameter with the correct address.

## How to Use

### General Page

This page displays the system identification of the transmitter (**System Name**, **System Contact**, **System Location**, **System Object ID**, **System Description**) and the **System Uptime**. The **System Name**, **System Contact**, and **System Location** parameters can be set from this page.

### Exciter Page

The **Exciter** table shows one row per exciter with its connection status, working state, status, output power, forward power, fan status, temperature and temperature status, time reference source, and the status of the reboot, firmware bank swap, and save default configuration commands.

### Amplifiers Page

The **Amplifier Number** parameter shows the number of amplifier modules installed. The **Amplifier Table** lists each module with its connection status, working state, RF status, forward power, total current, temperature, and PSU, fan, reflected-power, and temperature alarm and warning states.

### Power Management Page

This page shows the **Nominal Power** and the antenna and dummy-load forward and reflected power in mW, dBm, and percentage of nominal power. **Nominal Power** can be set from this page. **Power Derating** is calculated by the connector from the **Nominal Power** and the antenna **Forward Power dBm**.

Under **Power Thresholds**, the **Low Power Warning Threshold**, **Low Power Alarm Threshold**, **Reflected Power Warning Threshold**, and **Reflected Power Alarm Threshold** configured on the transmitter are displayed (read-only).

### Switch Page

This page controls exciter switchover. Use **Switch Mode**, **Switch Policy**, **Switch Delay**, and **Switch Restore Delay** to configure automatic or manual switching. The **Set Exciter A/B as Preferential** and **Enable/Disable Spare Exciter Maintenance** buttons send the corresponding commands to the transmitter; the current **Preferential Exciter** is shown as a read-only parameter.

The **Exciter Switched**, **Spare Exciter Availability**, and **Switch Fault** parameters reflect the current switch status.

### Inputs Page

This page shows the **Input Physical Interface Status** table, the **Input Selection** and **Input on Air**, and the input general status: **External Reference**, **10 MHz Reference Lock**, **Input Switch Hitless**, **Input Module Status**, **Auto Switch Reference Presence**, and **PPS Difference**.

The **Input Management Switch Mode** and **PPS Max Difference** (expressed in units of 10 ns, range 10 to 10000) can be configured from this page.

### System Page

This page shows the **Transmission Mode**, **Channel Frequency**, **Forward Power**, **Reflected Power**, **Load Forward Power**, **Load Reflected Power**, and the **Power Supply 1/2 Alarm**, **Lockout Alarm**, and **Interlock Alarm** states. All parameters on this page are read-only.

### Web Interface Page

The web interface is only accessible when the client machine has network access to the product.

The address used is taken from the **Web Interface** parameter on the **General** page (see [Initialization](#initialization)).

## Polling

The connector uses three timers:

| Timer | Interval | Data |
|--|--|--|
| Fast | 10 seconds | System uptime, antenna and load forward/reflected power |
| Medium | 30 seconds | Exciter table, amplifier table, input status, switch configuration and status, PSU, switch, and system alarms |
| Slow | 1 hour | System identification, nominal power, power thresholds, amplifier number |

## Notes

- As of version 1.0.0.6, **Forward Power dBm** is scaled to dBm instead of tenths of dBm. Trend history recorded before this version is in tenths of dBm, and alarm templates on this parameter should be reviewed.
- As of version 1.0.0.6, the **Exciter Output Power** unit is mW instead of dBm.
