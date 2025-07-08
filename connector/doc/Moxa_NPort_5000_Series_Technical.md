---
uid: Connector_help_Moxa_NPort_5000_Series_Technical
---

# Moxa NPort 5000 Series Connector

## About

The Moxa NPort 5000 Series Connector is a DataMiner driver designed to interface with the Moxa NPort device. It collects and visualizes comprehensive system, network, and serial communication metrics via SNMP, while also enabling device control features such as soft reset via Telnet.


## Version Info

| Range   | Key Features     | Based on | System Impact |
|---------|------------------|----------|----------------|
| 1.0.0.x | Initial version  | -        | -              |


## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

**SNMP CONNECTION:**

- **IP address/host**: The IP address of the Moxa NPort device.
- **Device address**: Not required.

**SNMP Settings:**

- **Port number**: 161 (default).

#### Telnet Connection – Moxa Telnet

This connector uses a Telnet connection to perform soft reset commands.

**TELNET CONNECTION:**
> [!NOTE]
> Telnet is only used to perform soft reset, not for polling data.

### Initialization

No additional configuration is required after element creation.

## How to Use

Once deployed, the connector polls SNMP parameters across multiple logical pages:
- **General Page**: System description, object ID, uptime, contact, name, location, number of services.
- **Interfaces Page**: Physical and virtual interface statistics.
- **IP Page**: Datagram, address translation, and discard statistics.
- **ICMP Page**: ICMP-related metrics like echo requests and responses.
- **UDP Page**: UDP datagram counters, errors, and traffic stats.
- **TCP Page**: Table of all active TCP connections and session-level metrics.
- **RS-232 Page**: RS-232 port information including synchronous/asynchronous port status.
- **Signal Page**: Input and output signal tables for RS-232 lines.
- **SNMP Page**: SNMP message statistics such as get, set, and trap counters.

Telnet connectivity enables remote soft resets, useful for troubleshooting or recovering unresponsive devices.

## Notes

- This connector supports standard MIBs provided by Moxa. Ensure the correct firmware version and SNMP agent are enabled on the device.
- The Telnet-based soft reset functionality must be explicitly enabled and accessible via the device configuration.
