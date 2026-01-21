---
uid: Connector_help_Linux_Platform
---

# Linux Platform

## About

This connector lets you monitor Linux servers using either SSH or SNMP. It is designed to be reliable: if one connection method fails, it can automatically try the other to keep your data flowing. It tracks everything from basic CPU and memory usage to specific hardware health for HP and Dell servers.

## Key Features

* **SSH & SNMP Failover**: Uses two ways to talk to your server so you don't lose visibility if a protocol is blocked.
* **HP and Dell**: Tracks fans, power supplies, and temperatures specifically for HP and Dell hardware.
* **Process Tracking**: A built-in Task Manager shows which apps are running and how much CPU they use.
* **Storage & Memory**: Monitors disk space, read/write speeds, and physical memory usage.
* **Network Stats**: Displays data rates for all network interfaces.

## Use Cases

### Use Case 1
**Challenge**: You have some servers that only allow SNMP and others that only allow SSH.
**Solution**: This connector handles both. It picks the best available method for each server.
**Benefit**: You use one tool to see all your Linux servers regardless of their communication protocol and security settings.

### Use Case 2
**Challenge**: A critical process crashes, and you don't find out until users complain.
**Solution**: You can set the connector to watch specific processes. If the process stops, it triggers an alarm.
**Benefit**: You can fix the process crash and restarting it before users notice a problem.

### Use Case 3
**Challenge**: Servers in a remote location might be overheating or having power issues.
**Solution**: The connector reads internal sensors for fans and power supplies on HP and Dell machines.
**Benefit**: You can replace a failing fan before the whole server shuts down from heat.

## Technical Reference

### Prerequisites

* **SNMP**: The IP, port (usually 161), and community strings.
* **SSH**: The IP, port (usually 22), and credentials: a username and password (usually port 22).
* **Vendor Agents**: For HP or Dell data, you need their management software (like Insight Agents or OpenManager) installed on the server.

> [!NOTE]
> For the full technical details and memory calculation logic, see the [technical documentation](xref:Connector_help_Linux_Platform_Technical).
