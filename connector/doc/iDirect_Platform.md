---
uid: Connector_help_iDirect_Platform
---

# iDirect Platform

## About

The iDirect Evolution NMS is a centralized interface for managing satellite communication networks. It provides real-time visibility into network health, remote terminal status, carrier configurations, and system performance.

The iDirect Platform connector provides the key data from iDirect Evolution NMS. The connector organizes data into logical sections for easy navigation and operational control of the complete NMS in a single element.

## Key Features

- **Remote terminal monitoring**: Detailed visibility into VSAT remotes, including operational state, uptime, configuration, and connectivity metrics.

- **Inroute group analytics**: Insights into burst traffic, actual capacity, available bandwidth, symbol rate distributions, and MODCOD compositions.

- **Network performance summary**: Bandwidth usage, upstream/downstream rates, booked capacity, QoS allocation, and MODCOD distribution across networks.

- **Linecard health and operations**: Status, temperature, power levels, error counters, carrier frequency assignments, and chassis slot mapping.

- **Polling and DVE status tracking**: Overview of line card polling state, DVE activation, and last active timestamps to ensure consistent monitoring.

## Use Cases

### Remote Terminal Troubleshooting

**Challenge**: Operators need to quickly troubleshoot issues affecting remote VSAT terminals across complex networks.

**Solution**: The connector centralizes remote operational metrics, including state, uptime, serial number, and management IP, into a single accessible view.

**Benefit**: Faster diagnosis, reduced downtime, and improved service reliability.

### Bandwidth and Capacity Optimization

**Challenge**: Bandwidth planning and optimization require accurate visibility into network utilization and inroute group behavior.

**Solution**: The connector provides granular capacity usage, traffic patterns, and MODCOD distribution across inroute groups and networks.

**Benefit**: Better capacity management, improved efficiency, and data-driven decision making.

### Hardware and Infrastructure Monitoring

**Challenge**: Ensuring optimal hardware performance requires continuous monitoring of line cards, carriers, and chassis health.

**Solution**: Linecard and chassis metrics, including temperatures, power levels, error rates, and slot assignments, are displayed clearly for monitoring.

**Benefit**: Increased hardware reliability, early issue detection, and simplified platform maintenance.

### Polling & DVE Monitoring

**Challenge**: Ensuring accurate and up-to-date network insights requires consistent polling across all line cards, but operators may lack visibility into which cards are actively polled or whether DVE is functioning correctly.

**Solution**: The Polling Configuration section provides a clear overview of the polling status, DVE state, and last active timestamps for every line card, allowing operators to quickly identify gaps or inactive components.

**Benefit**: Improved monitoring reliability, faster detection of inactive or misconfigured line cards, and enhanced confidence in the accuracy of collected performance data.

## Technical Reference

### Prerequisites

**Sufficient user permissions** are required to view operational metrics across remotes, networks, and hardware components.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_iDirect_Platform_Technical).
