---
uid: Connector_help_Observium_Network_Platform
---

# Observium Network Platform

## About

Observium is a network monitoring platform with auto-discovery that supports a wide range of device types, vendors, and operating systems. This connector integrates an Observium server into DataMiner through its REST API, providing a consolidated overview of the entire discovered device fleet.

## Key Features

- **Devices Overview**: Inventory of all devices known to Observium, keyed by hostname, including vendor, hardware, operating system, location, status, and uptime.

- **Fleet KPIs**: Total device count and live API connection state, with alarm monitoring.

- **Flexible authentication**: Supports both username/password (Basic) and API token authentication.

- **Polling Manager**: Per-poll enable/disable, configurable polling intervals, on-demand manual polling, and per-poll health status.

## Use Cases

### Centralized Multi-Vendor Network Inventory

**Challenge**: Network inventory discovered by Observium lives in a separate tool, outside the operational overview used by the operators.

**Solution**: The connector retrieves the full device inventory from the Observium API and presents it in DataMiner, where it can be used in dashboards, alarming, and reporting.

**Benefit**: Operators get a single pane of glass covering the Observium-discovered fleet alongside the rest of their DataMiner-monitored infrastructure.

### Health Surveillance of the Monitoring Platform

**Challenge**: When the monitoring platform itself becomes unreachable, this can go unnoticed, creating a blind spot.

**Solution**: The connector continuously reports the API connection state and raises alarms when communication with the Observium server fails.

**Benefit**: Issues with the Observium platform itself are detected and escalated like any other fault in the network.

## Technical Reference

### Prerequisites

- **Observium instance with the REST API enabled** is needed for the connector to retrieve data.
- **An Observium user account or API token with API access** is required for authentication.
- **Network access from the DataMiner Agent to the Observium web server** is required for polling.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Observium_Network_Platform_Technical).
