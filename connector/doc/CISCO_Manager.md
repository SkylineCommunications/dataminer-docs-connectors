---
uid: Connector_help_CISCO_Manager
---
# CISCO Manager

## About

The **CISCO Manager** connector provides centralized monitoring and management of Cisco network devices, including switches such as the Catalyst series, using SNMP, SSH, and HTTP.

This connector enables flexible access to device data and control functions, allowing network teams to monitor performance, retrieve operational data, and execute configuration actions across a wide range of Cisco devices.

### Key Features

- **Multi-protocol monitoring**: Collect data using SNMP, SSH, and HTTP, depending on device capabilities, ensuring broad compatibility across different Cisco platforms.
- **Flexible polling configuration**: Enable or disable specific parameter groups per device, allowing tailored monitoring while minimizing unnecessary load.
- **Interface performance tracking**: Monitor interface status, traffic, errors, and utilization to maintain optimal network performance.
- **Configuration and control operations**: Execute actions such as configuration backup/restore, ping diagnostics, and counter resets directly from DataMiner.

## Use Cases

### Minimize Downtime Through Proactive Health Monitoring

**Challenge**: Unexpected hardware or system failures on critical Cisco devices can lead to service interruptions and costly downtime.

**Solution**: Continuously monitor system health and hardware components such as fans, power supplies, and temperature sensors.

**Benefit**: Detect early signs of degradation or failures and take action before services are affected, reducing outages and improving overall uptime.

![FAN and PSU status information shown in a Cisco Manager element in DataMiner Cube](~/connector/images/CISCO_Manager_FAN.png)

### Optimize Network Traffic and Port Utilization

**Challenge**: Underused or overutilized interfaces can go unnoticed, leading to inefficient network performance or congestion at peak times.

**Solution**: Monitor all physical and virtual interfaces to track real-time port usage, errors, and throughput.

**Benefit**: Make informed decisions about load balancing, link upgrades, or port decommissioning, improving efficiency and performance without overprovisioning.

![Detailed interface information shown in a Cisco Manager element in DataMiner Cube](~/connector/images/CISCO_Manager_InterfaceOverview.png)

### Simplify VLAN and Trunk Configuration Management

**Challenge**: Managing VLAN assignments and trunk configurations across multiple switches can be complex and error-prone, especially when dealing with large VLAN ranges.

**Solution**: Streamline VLAN management, reduce configuration errors, and maintain consistent network segmentation across your infrastructure.

**Benefit**: Reduce time to resolution and restore services faster.

![VLAN information shown in a Cisco Manager element in DataMiner Cube](~/connector/images/CISCO_Manager_VLAN.png)

## Technical Reference

### Prerequisites

- SNMP (v2 or v3) enabled on target devices.
- Optional: SSH and HTTP enabled for extended functionality.
- Proper credentials configured for each protocol.

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for CISCO Manager, refer to the [technical help page](xref:Connector_help_CISCO_Manager_Technical).
