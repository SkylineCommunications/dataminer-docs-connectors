---
uid: Connector_help_Zabbix_Platform
---

# Zabbix Platform

## About

Zabbix is a monitoring platform that provides visibility into the health, performance, and availability of IT infrastructure, such as servers, networks, applications, services, and cloud resources.

The Zabbix Platform DataMiner connector leverages Zabbix's API to retrieve data from the Zabbix platform. This API is a web-based API that is shipped as part of the web frontend and uses the JSON-RPC 2.0 protocol.

This connector will export different [connectors](xref:Connector_help_Zabbix_Platform_-_Host) based on the retrieved hosts from the API.

## Key Features

- Provides host inventory and metadata (host groups, proxies, IPMI, maintenance status).
- Exposes monitoring elements such as Triggers, Items, Events, Correlations, and Problems.
- Filtering and navigation by host group and tag.

## Use Case

This connector is used to integrate Zabbix infrastructure monitoring into DataMiner:

- Centralize Zabbix host and health data in DataMiner management and dashboards.
- Drive automation or alerting workflows from Zabbix-triggered events/problems.
- Enable operations teams to inspect host status, triggers, items, and historical events from one interface.
- Migrate or augment existing Zabbix infrastructure visibility using DataMiner exported connectors.

## Technical Info

### Prerequisites

- Zabbix server with API enabled and reachable from DataMiner.
- DataMiner version 10.3 or higher is required for compatibility with the NetInsight Nimbra Vision connector.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Zabbix_Platform_Technical)