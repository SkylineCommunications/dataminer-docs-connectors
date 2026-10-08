---
uid: Connector_help_Tredess_MultiTX_Technical
---

# Tredess MultiTX

## About

The Tredess MultiTX is a modular DVB-T/DVB-T2 terrestrial transmitter platform. A chassis can contain transmitter (TX) modules, an NP1 redundancy switching unit, power supply units (PSU), and synchronization (SYNC/GNSS) modules.

This connector polls the device over SNMP and processes SNMP traps to monitor and configure all modules in the chassis.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Device address**: Not required.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

No additional configuration is required in a newly created element. Polling of the different data groups can optionally be tuned on the **Polling Settings** page.

To receive traps, configure the device to send SNMP traps to the IP address of the DataMiner Agent hosting the element.

### Web Interface

The web interface is only accessible when the client machine has network access to the product. The **Webpage** page of the element links directly to the device web interface using the polling IP.

## How to Use

The element data is organized in the following main page groups:

- **General**: High-level device identification and status overview.

- **Management**: Chassis management data, including System, Network, Modem, Battery, Date & Time, Device Info, I/O Interface, RF Monitor, Service, Status, Web, and Alarm/Event Configuration pages.

- **NP1**: The redundancy switching unit, with Device, Service, Setup (general settings, switching causes, 1+1 redundancy, automatic verifications), and Status pages.

- **PSU**: Power supply units, with Device, Service (power intake, cooling, fans), Setup, and Status pages.

- **SYNC**: Synchronization modules, with Device, GNSS 1, GNSS 2, Service, Setup, and Status pages.

- **TX Module**: Transmitter modules, with:

  - **Device**: Device info, alarms/events configuration, reset, software install, and DVB-T/DVB-T2 subpages (system, network, modulation, frame, and PLP settings).
  - **Input**: ASI 1/2 inputs, IP sockets, input switching configuration, and input switching status.
  - **IF Processor**: General, system, echo canceller, and precorrector settings.
  - **Modulator**: General modulator settings and precorrection.
  - **RF Output**: RF input/output configuration, output mutes, forward power, and amplifier data.
  - **Service**: Input level, power supply, cooling, and reference data.
  - **Status**: Module status overview.

- **Trap**: Received SNMP traps are processed and displayed on this page.

- **Polling Settings**: The Polling Manager table, where each poll group can be enabled/disabled and its polling interval adjusted. A context menu allows refreshing groups on demand.

Many parameters are monitored for alarming and trended, so historical data and alarm templates can be applied out of the box.

## Notes

- Trap processing is based on the wildcard trap OID `1.3.6.1.4.1.23180.2.1.1.4.10.*`; ensure the device firmware sends traps under this OID branch.
- Configuration changes performed outside DataMiner (e.g., via the device web interface) are picked up during the next poll cycle of the corresponding group.
