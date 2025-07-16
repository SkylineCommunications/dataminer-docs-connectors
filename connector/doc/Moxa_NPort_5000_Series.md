---
uid: Connector_help_Moxa_NPort_5000_Series
---

# Moxa NPort 5000 Series

## About

The Moxa NPort 5000 Series connector enables comprehensive monitoring and control using SNMP and Telnet, providing access to device status, network statistics, RS-232 port information, and signal activity. In addition to passive monitoring, the connector supports Telnet-based soft resets for proactive remote device management.

## Key Features

- **Multi-protocol communication**: Leverages both SNMP for polling and Telnet for command execution (e.g. soft reset), maximizing control capabilities.

- **Comprehensive parameter coverage**: Provides detailed data on system, interface, IP, ICMP, UDP, TCP, and SNMP performance.

- **RS-232 monitoring**: Monitors both synchronous and asynchronous RS-232 ports, with input and output signal tables.

- **Connection tracking**: Displays all active TCP connections, aiding in network diagnostics and traffic monitoring.

- **Soft reset via Telnet**: Enables remote rebooting of the device through Telnet commands, reducing on-site intervention needs.

## Use Cases

### Use Case 1

**Challenge**: Operators need real-time visibility on serial-to-Ethernet converters deployed across multiple remote sites.

**Solution**: The connector gathers comprehensive SNMP-based metrics across system, IP, and RS-232 domains, ensuring consistent monitoring.

**Benefit**: Reduces manual diagnostics by centralizing key performance indicators within DataMiner.

### Use Case 2

**Challenge**: Remote devices occasionally become unresponsive, requiring physical resets.

**Solution**: Via the Telnet connection, the connector allows you to execute a soft reset remotely.

**Benefit**: Minimizes downtime and eliminates costly technician dispatches.

### Use Case 3

**Challenge**: Troubleshooting network latency issues caused by excessive TCP connections.

**Solution**: The TCP page provides a real-time view of all open TCP connections and associated traffic.

**Benefit**: Empowers teams to identify and resolve communication bottlenecks quickly.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Moxa_NPort_5000_Series_Technical).
