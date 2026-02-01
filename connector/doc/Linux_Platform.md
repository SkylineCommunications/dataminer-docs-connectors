---
uid: Connector_help_Linux_Platform
---

# Linux Platform

## About

The Linux Platform connector allows users to achieve comprehensive, real-time monitoring of their Linux-based servers. Leveraging Linux system tools and commands, this connector provides deep visibility on system performance, health metrics, and operational status, ensuring proactive management and swift issue resolution.

## Key Benefits

- **Broad compatibility**: Supports a wide range of Linux distributions, ensuring seamless integration across diverse server environments.

- **Comprehensive monitoring**: Captures a wide array of performance indicators, including CPU usage, memory consumption, disk activity, network interfaces, and running processes.

- **Scalable integration**: Designed to integrate effortlessly within the DataMiner ecosystem, enabling centralized monitoring and management of IT infrastructures.

- **Security and compliance**: Utilizes secure SSH connections, aligning with organizational security protocols and compliance requirements. Additionally, it supports SNMP for environments where SSH access is restricted.

## Use Cases

### Comprehensive Server Performance Monitoring

The connector utilizes standard Linux commands to collect key performance indicators from servers running various Linux distributions. This includes monitoring CPU usage, memory consumption, disk activity, and network interface statistics.

![Linux Platform Performance Monitoring](~/connector/images/linux_platform_marketing_performance_monitoring.png)

### Process and Task Monitoring

Through the process management capabilities, the connector provides a detailed view of all processes running on the monitored server. Administrators can track active processes, monitor their resource usage, and set up alarms for specific process behaviors, such as unexpected terminations or high resource consumption. This facilitates efficient process management and ensures critical applications remain operational.

Additionally, the connector supports tracking specific processes by name, enabling you to monitor their availability and receive alerts when they stop or fail to start.

![Linux Platform Process Management](~/connector/images/linux_platform_marketing_process_monitoring.png)

### Network Interface and Port Monitoring

The connector enables monitoring of network adapters, providing data on bandwidth utilization and adapter status. Additionally, it offers port monitoring capabilities to verify whether specific ports are open or closed and to measure response delays. This is crucial for ensuring network connectivity and diagnosing potential communication issues.

![Linux Platform Network Monitoring](~/connector/images/linux_platform_marketing_network_interfaces.png)

### Hardware Health Monitoring

For servers manufactured by Dell and HP, the connector provides hardware-specific monitoring features. This includes tracking parameters like temperature, power supply status, fan speeds, CPU health, and memory information. Such detailed hardware monitoring helps in maintaining optimal operating conditions and preventing hardware failures.

## Technical Reference

### Prerequisites

- **SSH access**: The connector relies on SSH for data collection, so the target machines must have SSH enabled and accessible.
- **SNMP access**: If SNMP is used as the communication protocol, ensure that the SNMP agent is properly configured on the target Linux machines.

> [!NOTE]
> For detailed technical information, refer to out [technical information](xref:Connector_help_Linux_Platform_Technical)
