---
uid: SatPort_Incident_Manager
---

# SatPort Incident Manager

## About

The purpose of this connector is to listen to the ticketing application.  
When a new ticket is detected, it automatically attempts to forward it to iPaaS (Integration Platform as a Service).

## Key Features

- **Ticket Subscription**  
  The connector allows you to subscribe to specific ticket types via a configuration table. Only tickets of the selected types will be considered.

- **Automatic Ticket Forwarding**  
  If a ticket matches one of the subscribed types, it will be sent to iPaaS for further processing.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:SatPort_Incident_Manager_Technical).
