---
uid: Connector_help_Zabbix_Platform
---

# Zabbix Platform

## About

Zabbix is a monitoring platform that provides visibility into the health, performance, and availability of IT infrastructure, such as servers, networks, applications, services, and cloud resources.

The Zabbix Platform DataMiner connector leverages Zabbix's API to retrieve data from the Zabbix platform. This API is a web-based API that is shipped as part of the web frontend and uses the JSON-RPC 2.0 protocol.

This connector will export different [connectors](xref:Connector_help_Zabbix_Platform_-_Host) based on the retrieved hosts from the API.

## Key Features
- Discover and import Zabbix hosts automatically into DataMiner as managed elements.
- View host status, uptime, and monitoring health from the DataMiner UI.
- Drill into host groups, triggers, items, events, correlations, and problem records.
- Enable/disable host polling and configure per-host DVE behavior.
- Apply host-group and tag filters for fast navigation and operational focus.
- Link Zabbix-generated issues into DataMiner automation workflows and alerting.

## Use Case

### Unified Monitoring Visibility
- **Challenge:** siloed Zabbix monitoring data separated from remaining network and workflows.
- **Solution:** export Zabbix monitoring data to DataMiner as elements.
- **Benefit:** unified visibility for NOC teams and reduced context switching.

### Automation and Event Correlation
- **Challenge:** manual correlation of Zabbix events and automated workflows.
- **Solution:** map Zabbix Triggers/Events into DataMiner and route to automation/alert pipelines.
- **Benefit:** faster incident response and fewer missed issues.



## Technical Info

### Prerequisites

- Zabbix server with API enabled and reachable from DataMiner.
- DataMiner version 10.3 or higher is required for compatibility with the NetInsight Nimbra Vision connector.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Zabbix_Platform_Technical)