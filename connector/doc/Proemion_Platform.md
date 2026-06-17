---
uid: Connector_help_Proemion_Platform
---

# Proemion Platform

## About

The **Proemion Platform** Connector integrates the Proemion cloud-based telematics platform into DataMiner, enabling centralized monitoring, data aggregation, and operational insight for connected industrial machines. The connector provides a scalable and structured view of large fleets of geothermal drilling machines and associated communication units.

## Key Features

- **Machine Inventory**: Track all connected geothermal drilling machines, enriched with machine metadata, and connection status with the Proemion Data Platform.

- **Geo Location Tracking**: Monitor the physical location of machines, providing GPS-based insights into machine positioning to support fleet tracking, site operations, and logistics optimization.

- **Flexible Machine Polling**: Enable or disable monitoring per machine to optimize API usage and focus on critical equipment.

- **Communication Unit Monitoring**: Monitor communication hardware linked to machines, including connection status.

- **Comprehensive Telemetry (Measurements)**: Access real-time and historical telemetry operational metrics such as pressures, temperatures, drilling performance indicators, and other machine-specific sensor data.

- **Event Monitoring and Alerting**: Track machine activity, warnings, and faults. Events are translated into DataMiner alarms, allowing operators to quickly detect and respond to issues in the field.

- **Firmware Management Visibility**: Monitor firmware versions and updates to ensure all machines and communication units are running supported and up-to-date software versions.

- **Overview Tree Navigation**: The connector provides an overview tree control that organizes all data hierarchically across Organizations, Machines, and related entities. This allows operators to quickly navigate large datasets, drill down from high-level organizational structures to individual machines, and efficiently locate telemetry, events, geo location and communication units details for each machine from a single interface.


## Use Cases

### Geothermal Fleet Monitoring

**Challenge**: Operators managing fleets of geothermal drilling machines across multiple sites face challenges in tracking machine status, location, and performance. Limited visibility often leads to inefficient operations, delayed issue detection, and increased downtime.

**Solution**: This connector centralizes all machine data into DataMiner using structured tables and tree view. Operators can monitor the status, position, and performance of all drilling machines in real time, while Communication Units ensure visibility into connectivity health.

**Benefit**: Improve operational efficiency through real-time fleet visibility, reduce downtime by detecting connectivity or machine issues early, and optimize machine utilization across sites.

### Machine Health Monitoring and Event Tracking

**Challenge**: Unexpected machine failures and lack of insight into operational anomalies can lead to costly downtime and reactive maintenance.

**Solution**: The connector continuously monitors machine telemetry and system-generated events. DataMiner alarms are triggered when abnormal values or critical events are detected.

**Benefit**: Enable proactive maintenance by identifying issues before failure occurs, reduce unplanned downtime, and improve overall equipment reliability.

### Multi-Organization Asset Management

**Challenge**: Service providers managing machines across multiple customers or business units need a structured way to separate and monitor assets while maintaining a unified overview.

**Solution**: The connector allows to group assets/machines logically into Organizations.

**Benefit**: Achieve scalable and structured asset management across multiple organizations, ensuring clear visibility and control while maintaining separation of data contexts.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Proemion_Platform_Technical).
