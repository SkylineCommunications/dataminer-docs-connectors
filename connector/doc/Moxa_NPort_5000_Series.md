---
uid: Connector_help_Moxa_NPort_5000_Series
---

# Moxa NPort 5000 Series Connector

## About

The Moxa NPort 5000 Series Connector enables comprehensive monitoring and control using SNMP and Telnet, providing access to device status, network statistics, RS-232 port information, and signal activity. In addition to passive monitoring, the connector supports Telnet-based soft resets for proactive remote device management.

## Key Features

- **Multi-Protocol Communication**: Leverages both SNMP for polling and Telnet for command execution (e.g., soft reset), maximizing control capabilities.

- **Comprehensive Parameter Coverage**: Provides detailed data on system, interface, IP, ICMP, UDP, TCP, and SNMP performance.

- **RS-232 Monitoring**: Monitors both synchronous and asynchronous RS-232 ports, with input and output signal tables.

- **Connection Tracking**: Displays all active TCP connections, aiding in network diagnostics and traffic monitoring.

- **Soft Reset via Telnet**: Enables remote rebooting of the device through Telnet commands, reducing on-site intervention needs.

## Use Cases

### Use Case 1

**Challenge**: Operators need real-time visibility into serial-to-Ethernet converters deployed across multiple remote sites.

**Solution**: The connector gathers comprehensive SNMP-based metrics across system, IP, and RS-232 domains, ensuring consistent monitoring.

**Benefit**: Reduces manual diagnostics by centralizing key performance indicators within DataMiner.

### Use Case 2

**Challenge**: Remote devices occasionally become unresponsive, requiring physical resets.

**Solution**: Using the Telnet connection, the connector enables remote execution of a soft reset.

**Benefit**: Minimizes downtime and eliminates costly technician dispatches.

### Use Case 3

**Challenge**: Troubleshooting network latency issues caused by excessive TCP connections.

**Solution**: The TCP page provides a real-time view of all open TCP connections and associated traffic.

**Benefit**: Empowers teams to identify and resolve communication bottlenecks quickly.

## Technical Reference

### Prerequisites

- **SNMP access** is needed for real-time polling of performance and network statistics.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Moxa_NPort_5000_Series_Technical).
