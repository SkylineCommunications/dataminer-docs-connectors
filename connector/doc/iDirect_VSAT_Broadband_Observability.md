---
uid: Connector_help_iDirect_VSAT_Broadband_Observability
---

# iDirect VSAT Broadband Observability

## About

The iDirect VSAT Broadband Observability connector provides real-time network insights for VSAT broadband systems. Built on the iDirect NMS platform, this connector aggregates critical performance data across networks at a teleport, enabling users to monitor, analyze, and optimize broadband connectivity through a low-code app.

## Key Features

- **Comprehensive network monitoring**: Tracks network health, congestion, and site availability in real time.

- **Traffic and capacity analysis**: Monitors bandwidth utilization, providing visibility on upstream and downstream traffic.

- **Site count monitoring**: Uses both state change logs and event message logs to determine site status with high accuracy.

- **Automated data collection**: Seamlessly integrates with MySQL databases to retrieve and update data without manual intervention.

- **Configurable thresholds and alerts**: Allows users to customize bandwidth configurations and proactively detect network congestion.

## Use Cases

### Real-Time Network Health Monitoring

**Challenge**: Managing VSAT broadband networks across multiple locations requires real-time insights to detect connectivity issues before they impact operations.

**Solution**: The connector continuously collects and aggregates data from the MySQL database, providing instant visibility into network health, congestion, and site status.

**Benefit**: Proactive network management reduces downtime and improves service reliability.

### Bandwidth Optimization for High-Traffic Networks

**Challenge**: Unpredictable bandwidth consumption leads to network congestion, affecting performance and user experience.

**Solution**: By monitoring bandwidth utilization against the configured values, the connector helps identify capacity issues and optimize network traffic distribution.

**Benefit**: Improved network efficiency ensures seamless communication and maximized resource utilization.

### Monthly Network Performance Reporting

**Challenge**: Gathering and analyzing large volumes of network data for performance reports is time-consuming and complex.

**Solution**: The connector automates data collection, calculates 95th percentile bandwidth usage, and generates reports on network utilization.

**Benefit**: Simplified reporting saves time, enhances decision-making, and ensures data accuracy.

## Technical Reference

### Prerequisites

**Database Access**: Credentials for accessing the MySQL database containing network data.

**Configuration Server**: Required to retrieve teleport, network, and net modem configurations.

**Archive Server**: Needed for event message logs and historical data retrieval.
