---
uid: Connector_help_SatPort_Incident_Manager
---

# SatPort Incident Manager

## About

The purpose of this connector is to listen to the ticketing application. When a new ticket is detected, the connector automatically attempts to forward it to iPaaS (Integration Platform as a Service).

## Key Features

- **External owner registration**: On startup, the connector registers its element name as an external owner within the ticketing application. This allows users to explicitly assign tickets to the connector.

- **Automatic ticket forwarding**: When a ticket's external owner matches the connector’s element name, it is automatically forwarded to iPaaS. iPaaS then creates the corresponding record in ServiceNow, ensuring that both systems stay in sync.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_SatPort_Incident_Manager_Technical).
