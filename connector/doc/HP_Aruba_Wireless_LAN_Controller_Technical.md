---
uid: Connector_help_HP_Aruba_Wireless_LAN_Controller_Technical
---

# HP Aruba Wireless LAN Controller Technical Documentation

## About

The HP Aruba Wireless LAN Controller connector monitors Aruba wireless controllers using SNMP. It provides visibility into controller health, managed access points, connected wireless clients, memory usage, CPU utilization, interface statistics, and licensing information.

## Configuration

### Connections

#### SNMP Connection - Controller Monitoring

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: Management IP address or hostname of the Aruba Wireless LAN Controller.
- **Device address**: Not required.

SNMP Settings:

- **Port number**: 161 (default).
- **Get community string**: Community string used to retrieve monitoring data from the controller.
- **Set community string**: Not used by this connector.

### Initialization

No additional configuration is required after element creation. Once SNMP connectivity is established, the connector automatically retrieves and displays the available controller information.

## How to Use

The connector organizes monitoring information across the following pages: **General**, **Access Points**, **Clients**, **Memory**, **CPU**, **Interfaces**, **License**, and **Web Interface**.

### General

The General page provides high-level controller health and identification information, including:

- System Name
- Object ID
- System Uptime
- Switch MAC Address
- Internal Temperature
- Supervisor Card CPU Usage
- RAM Memory Usage
- Flash Memory Usage

### Access

The Access Points page contains detailed information about all wireless access points managed by the controller.

### Clients

The Clients page displays wireless station information, including all available client-related statistics and operational data.

### Memory

The Memory page provides memory utilization information through:

- Device Memory table
- Memory Status table

The Memory Status table displays total available memory and remaining free memory.

### CPU

The CPU page contains the CPU Usage table, displaying processor utilization statistics per process.

### Interfaces

The Interfaces page displays interface-related information and statistics for all monitored interfaces on the controller.

### License

The License page contains the Switch Licenses table, displaying license information and status for the controller.
### Wwb Interface Page

## Notes

The connector is intended for monitoring purposes and relies on SNMP polling to retrieve controller statistics and operational information.

Monitoring capabilities depend on the SNMP information exposed by the specific Aruba controller model and software version.
