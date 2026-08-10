---
uid: Connector_help_Observium_Network_Platform
---

# Observium Network Platform

## About

Observium is a network monitoring platform with auto-discovery that supports a wide range of device types, vendors, and operating systems. This connector integrates an Observium server with DataMiner through its REST API, providing a consolidated overview of the entire discovered device inventory.

## Key Features

- **Devices Overview**: Inventory of all devices known to Observium, displayed by hostname, including vendor, hardware, operating system, location, status, and uptime.

- **Platform KPIs**: Total device count and API connection state, refreshed on each poll cycle. By default, the connection state raises an alarm when communication with the Observium server fails. The device count can be monitored with user-defined alarm thresholds.

- **Flexible authentication**: Supports both username/password (HTTP Basic) and API token authentication.

- **Polling Manager**: Per-poll enable/disable settings, configurable polling intervals, on-demand manual polling, and per-poll health status.

## Use Cases

### Centralized Multi-Vendor Network Inventory

**Challenge**: The network inventory discovered by Observium resides in a separate tool, outside the operational overview used by operators.

**Solution**: The connector retrieves the full device inventory from the Observium API and presents it in DataMiner, where it can be used in dashboards, alarming, and reporting.

**Benefit**: Operators get a single pane of glass that combines the Observium-discovered inventory with the rest of their DataMiner-monitored infrastructure.

### Health Surveillance of the Monitoring Platform

**Challenge**: If the monitoring platform itself becomes unreachable, this may go unnoticed, creating a blind spot.

**Solution**: The connector reports the API connection state on every poll cycle and raises alarms when communication with the Observium server fails. The polling interval is configurable, so the detection time can be tuned to the desired responsiveness.

**Benefit**: Issues with the Observium platform itself are detected and escalated like any other fault in the network.

## Technical Reference

### Prerequisites

- **Observium Subscription Edition (Professional or Enterprise)** is required. The Observium REST API is only included in the paid Subscription Editions and is not available in the free Community Edition.

- **An Observium user account or API token with API access** is required for authentication. To retrieve the complete device inventory, the account (or the account backing the token) must have at least user level 5 (*Global Read*). Accounts with a lower level only return the devices explicitly permitted to them, resulting in an incomplete inventory.

- **Network access from the DataMiner Agent to the Observium web server** is required for polling.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Observium_Network_Platform_Technical).
