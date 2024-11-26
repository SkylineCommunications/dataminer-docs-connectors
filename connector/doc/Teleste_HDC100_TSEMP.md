---
uid: Connector_help_Teleste_HDC100_TSEMP
---

# Teleste HDC100 TSEMP

## About

The **Teleste HDC100 TSEMP connector** is an efficient solution for managing and monitoring HDO modules within the Teleste HDO platform. The HDC100 module, installed within an HDX frame, enables centralized control over Teleste’s HDO modules—including transmitters, receivers, and more—through real-time health monitoring and remote access. This connector offers streamlined oversight by displaying the status of all connected modules, complete with essential metrics such as configuration, software version, uptime, and reset options for intuitive use. The system allows seamless Ethernet and serial connectivity, compatible with the Teleste CATVisor Commander and EMS.

### Key Features

- **Real-time module status**: View connected HDO modules with real-time health information, emphasizing key metrics for quick insights and diagnostics.
- **Essential device information access**: Quickly access configuration, software versions, uptime data, and reset functionalities, ensuring efficient module management.
- **Detailed network configuration**: Configure IP settings, network masks, and gateway parameters to ensure smooth network connectivity across the HDO modules.
- **Scalable integration**: Supports up to 16 racks of HDO modules, offering flexible scalability and adaptation for expanding system demands.

> [!NOTE]
> The complete list of supported modules and additional technical details are available on the [Technical help page](xref:Connector_help_Teleste_HDC100_TSEMP_Technical).

## Use Cases

### Remote Monitoring of Device Alarms

**Challenge:** In large, distributed systems, monitoring and managing device alarms remotely can be a challenge, particularly for maintaining system reliability.

**Solution:** The **Teleste HDC100 TSEMP** connector allows users to remotely set and manage alarm thresholds for analog signals, including HiHi, Hi, Lo, and LoLo limits. This feature enables proactive monitoring and reduces the risk of unexpected system failures.

**Benefit:** Users can **quickly address potential issues** in real time, improving the reliability and performance of their network operations.

![Analog Alarm Limits](~/connector/images/TelesteHDC100MonitoringAnalogAlarmLimits.png)

---

### Efficient Management of Discrete Alarms

**Challenge:** Managing discrete (binary) alarms across multiple Teleste HDC100 modules can be resource-intensive without a unified solution.

**Solution:** The **Teleste HDC100 TSEMP** connector provides centralized control over discrete alarms, allowing users to configure alarms for individual modules based on specific operational needs.

**Benefit:** Users can achieve **better system oversight** and targeted management of discrete alarms, reducing complexity and enhancing operational efficiency.

![Discrete Alarm Limits](~/connector/images/TelesteHDC100MonitoringDiscreteAlarms.png)

---

## Technical info

### Prerequisites

- **DataMiner version 10.2 or higher** is required for compatibility with the Teleste HDC100 TSEMP connector.
- **Administrator permissions** are needed to configure Teleste HDC100 modules through the connector.
- **Network and serial access** to the Teleste HDC100 modules are essential, including IP address, default ports (2500 for main connection, 65535 for modules), and serial communication capabilities.

> [!NOTE]
> For in-depth information on configuring and using the DataMiner connector for Teleste HDC100, refer to the [Technical help page](xref:Connector_help_Teleste_HDC100_TSEMP_Technical).