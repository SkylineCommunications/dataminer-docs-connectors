---
uid: Connector_help_SatPort_Incident_Manager
---

# SatPort Incident Manager

## About

The purpose of this connector is to listen to the ticketing application. When a new ticket is detected, the connector automatically attempts to forward it to iPaaS (Integration Platform as a Service).

## Key Features

- **External Owner Registration**  
  On startup, the connector registers its element name as an *External Owner* within the ticketing application. This allows users to explicitly assign tickets to the connector.

- **Automatic Ticket Forwarding**  
  When a ticket’s *External Owner* matches the connector’s element name, it is automatically forwarded to iPaaS.  
  iPaaS then creates the corresponding record in ServiceNow, ensuring both systems stay in sync.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_SatPort_Incident_Manager_Technical).
