---
uid: Connector_help_iDirect_Intuition
description: "Monitor ST Engineering iDirect Intuition satellite ground systems in DataMiner with visibility into inventory, alarms, events, topology, and performance."
---

# iDirect Intuition

## About

The ST Engineering iDirect Intuition connector provides centralized visibility into an Intuition satellite ground system. It brings configuration, inventory, operational status, alarms, events, topology, and performance information together in DataMiner, helping operations teams understand service health and the relationships between managed entities.

By presenting Intuition resources in an organized, object-based structure, the connector helps operators navigate large environments, identify affected services, and investigate issues at the relevant terminal, network, or infrastructure level.

## Key Features

- **Monitor the Intuition ground system**: Monitor terminals, iNets, satellites, service plans, network resources, and supporting infrastructure from a centralized interface.
- **Work with dedicated Terminal and iNet DVEs**: Represent terminals and iNets as DataMiner Dynamic Virtual Elements (DVEs), providing object-specific monitoring and navigation across large satellite environments.
- **Understand service and infrastructure relationships**: Visualize relationships between terminals, network resources, services, satellites, and infrastructure components to assess dependencies and support root cause investigation.
- **Track configuration and operational state**: Maintain visibility into managed object inventory, configuration state, operational state, and associated status information across the Intuition environment.
- **Review events, alarms, and performance data**: Bring Intuition events, alarms, and operational metrics into a unified view to support service assurance and performance analysis.

## Use Cases

### Monitor Remote Satellite Terminals

Operations teams can review the state and performance of individual terminals through dedicated Terminal DVEs, while retaining visibility on the wider Intuition environment.

### Assess iNet Health and Dependencies

Teams can use iNet DVEs and relationship-aware views to understand how terminals, services, satellites, and network resources are connected when investigating service-impacting issues.

### Maintain an Accurate Operational Inventory

Configuration and inventory data can be consolidated in DataMiner to provide a consistent view of the Intuition objects managed across the ground system.

### Investigate Service-Impacting Events

Operators can correlate object relationships, operational status, alarms, events, and performance information to narrow down the potential source and impact of an issue.

## Prerequisites

- Access to an ST Engineering iDirect Intuition deployment.
- Access to the Intuition GraphQL API.
- Appropriate API credentials and permissions for the information monitored by the connector.
