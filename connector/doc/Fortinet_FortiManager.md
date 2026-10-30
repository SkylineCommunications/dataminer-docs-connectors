---
uid: Connector_help_Fortinet_FortiManager
description: "Explore key features, use cases, and technical details of the Fortinet FortiManager connector for monitoring security infrastructure using DataMiner."
---

# Fortinet FortiManager

## About

Fortinet FortiManager provides centralized management of Fortinet security infrastructure. The DataMiner connector uses SNMPv2 to monitor the management server, its managed devices, and its administrative domains, bringing operational health, configuration status, and license expiration information into a single view.

## Key Features

- **System health monitoring**: Monitor CPU usage, memory consumption, disk usage, uptime, firmware version, and log rate.
- **Managed device and domain visibility**: View device inventory, connectivity, configuration state, and administrative domain membership, alongside domain status and capacity information.
- **License expiration tracking**: Track expiration dates for antivirus, intrusion prevention, web content filtering, and antispam licenses on managed devices.
- **Hardware and high-availability monitoring**: Monitor RAID status, individual disks, power supplies, HA mode, and HA peer status.
- **IP session visibility**: Inspect session protocols, source and destination IP addresses, ports, and expiration times.

## Use Cases

### Identify Infrastructure Health Issues

**Challenge**: Resource constraints, storage faults, or degraded redundancy can affect the availability of the security management environment.

**Solution**: Bring CPU, memory, disk, RAID, power supply, and HA information into DataMiner. Configure DataMiner alarming around the monitored parameters to match operational requirements.

**Benefit**: You can identify deteriorating conditions earlier and prioritize investigation and maintenance.

### Maintain Visibility Across Managed Devices and Domains

**Challenge**: Tracking device connectivity and configuration status becomes more difficult as the number of managed devices and administrative domains grows.

**Solution**: Use the connector's device and administrative domain tables to review inventory, domain membership, connection state, database state, configuration state, and policy package state.

**Benefit**: You get a consolidated view to identify disconnected devices and investigate configuration inconsistencies.

### Plan Security License Renewals

**Challenge**: License expiration dates distributed across multiple devices are difficult to track manually, increasing the risk of missed renewals.

**Solution**: Collect antivirus, intrusion prevention, web content filtering, and antispam license expiration dates in the managed device table.

**Benefit**: Facilitates renewal planning and helps reduce the risk of interruptions to licensed security services.

## Technical Reference

### Prerequisites

- **DataMiner 10.4.0.0 - 14003** or later.
- **An SNMPv2-enabled Fortinet FortiManager server** exposing the relevant FORTINET-FORTIMANAGER-FORTIANALYZER-MIB objects is needed for monitoring.
- **Network access and a valid SNMP read community string** are required for DataMiner to poll the server.

### Supported Firmware

Connector range **1.0.0.x** supports FortiManager firmware **5.6.8**.

### Connectivity

Configure the FortiManager polling IP address or hostname, SNMP port, and community strings during element creation. A valid set community string is needed when using writable parameters.

For trap-driven refreshes, configure FortiManager to send SNMP traps to DataMiner. Supported HA switch, RAID status change, and CPU threshold traps trigger polling of the corresponding data.

The embedded web interface requires network access from the client machine to the FortiManager server.

### Version 1.0.0.2

Version **1.0.0.2** is based on **1.0.0.1** and records the connector's migration to GitHub. This new version was required to restore availability in the DataMiner Catalog. Version 1.0.0.1 is not available in the Catalog.
