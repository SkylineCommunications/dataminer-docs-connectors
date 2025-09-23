---
uid: Connector_help_CISCO_XROS_Manager
---

# CISCO XROS Manager

## About

The **CISCO XROS Manager** connector provides centralized, real-time monitoring and management of CISCO ASR devices using the OpenConfig standard and gNMI. This solution enables streamlined access to structured telemetry data, including interface metrics, system health, LLDP information, and more, through secure and automated data collection.

### Key Features

- **System health monitoring**: Get a clear view of each router's overall health and uptime using real-time data from the system-level metrics. Stay informed about how your network infrastructure is performing at a glance.
- **Interface performance tracking**: Continuously monitor the status and performance of every network interface, including the port usage, speed, and error rates, to ensure smooth data flow across your organization.
- **Hardware component oversight**: Gain visibility on the physical components of your routers (fans, power supplies, temperature sensors, etc.) so potential hardware issues can be detected before they cause downtime.
- **Network topology awareness (LLDP)**: Automatically map how devices are connected through the network using LLDP (Link Layer Discovery Protocol) data. This helps visualize dependencies and identify misconfigurations quickly.

## Use Cases

### Minimize Downtime Through Proactive Health Monitoring

**Challenge**: Unexpected hardware or system failures on critical ASR routers can lead to service interruptions and costly downtime.

**Solution**: This connector continuously monitors system health and hardware components such as fans, power supplies, and temperature sensors using OpenConfig /system and /components data.

**Benefit**: Detect early signs of degradation or failures and take action before services are affected. This reduces emergency outages and boosts overall uptime.

![Power Supplies](~/connector/images/CISCO_XROS_Manager_PSU.png)

### Optimize Network Traffic and Port Utilization

**Challenge**: Underused or overutilized interfaces can go unnoticed, leading to inefficient network performance or congestion at peak times.

**Solution**: Monitor all physical and virtual interfaces via the /interfaces path to track real-time port usage, errors, and throughput.

**Benefit**: Make informed decisions about load balancing, link upgrades, or port decommissioning, improving efficiency and performance without overprovisioning.

![Interfaces](~/connector/images/CISCO_XROS_Manager_Interfaces.png)

### Accelerate Root Cause Analysis in Network Incidents

**Challenge**: Troubleshooting connectivity or performance issues often takes hours when there is a lack of visibility on device connections.

**Solution**: This connector uses LLDP data to show how devices are linked across the network, enabling quick tracing of affected paths.

**Benefit**: Reduce time-to-resolution by pinpointing the source of an issue within minutes instead of hours, resulting in faster service restoration.

![LLDP](~/connector/images/CISCO_XROS_Manager_LLDP.png)

## Technical Reference

### Prerequisites

- gNMI and OpenConfig telemetry enabled on target devices.
- DataMiner version **10.3.3.0 - 12753** or higher.
- Communication Gateway DxM version **1.2.2** or higher.
- Ensure proper firewall and routing rules are in place for telemetry data flow.

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for CISCO XROS Manager, refer to the [Technical help page](xref:Connector_help_CISCO_XROS_Manager_Technical).
