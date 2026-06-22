---
uid: Connector_help_MyUplink_Platform
---

# MyUplink Platform

## About

The **MyUplink Platform** connector integrates the MyUplink cloud platform into DataMiner, enabling monitoring, control, and data aggregation of connected HVAC and energy systems (e.g., heat pumps, indoor climate systems). The connector communicates with the MyUplink REST API, retrieves device and parameter data, and maps this information into DataMiner elements and parameters.

## Key Features

- **Comprehensive device inventory**: Monitor all MyUplink-connected devices including heat pumps, ventilation systems, and smart home equipment with detailed information on connection status, firmware versions, and serial numbers.

- **Hierarchical organization**: Organize devices into logical groups with a tree-based navigation structure for easy access to hundreds or thousands of devices.

- **Flexible device polling**: Enable or disable monitoring per device to optimize API usage and focus on critical equipment.

- **Smart home mode control**: Easily switch between Normal, Away, and Vacation modes to optimize energy consumption based on occupancy.

- **Aid mode control**: Manage auxiliary heating/cooling operations with automatic alarming when activated.

- **Indoor air quality monitoring**: Track CO₂ levels and humidity across zones to maintain healthy indoor environments.

- **Comprehensive parameter monitoring and control**: Access all device data points and configure parameters with built-in range constraints based on device capabilities.

- **Weekly schedule management**: View and manage time-based device schedules for automated operation throughout the week.

## Use Case: HVAC Fleet Management

**Challenge**: Facility managers operating distributed heat pump installations across multiple buildings or sites struggle with manual equipment checks, delayed fault detection, and lack of centralized visibility. Without real-time monitoring, equipment failures can go unnoticed for hours or days, leading to tenant complaints, energy waste, and costly emergency repairs.

**Solution**: The MyUplink Platform connector consolidates all heat pump data into a single platform with hierarchical device grouping, real-time connection monitoring, and automatic alarming. Operators can view the status of hundreds of devices at a glance, receive immediate notifications when units disconnect, track firmware versions across the fleet, and enable/disable polling for specific devices to focus resources on critical equipment.

**Benefit**: Reduce equipment downtime through instant fault detection, eliminate manual site visits for routine status checks, ensure consistent firmware compliance across all installations, and improve tenant satisfaction with proactive maintenance.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_MyUplink_Platform_Technical).
