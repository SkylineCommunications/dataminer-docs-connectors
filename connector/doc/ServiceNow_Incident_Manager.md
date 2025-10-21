---
uid: Connector_help_ServiceNow_Incident_Manager
---

# ServiceNow Incident Manager

## About

The **ServiceNow Incident Manager** connector acts as a bridge between the internal ticketing application and ServiceNow.  
It automatically creates incidents in ServiceNow whenever new tickets are generated in the ticketing system and keeps both platforms synchronized by applying updates made on the ServiceNow side back to the ticketing application.  

This ensures a consistent and up-to-date view of all incidents across both systems, without requiring manual intervention.

## Key Features

- **External Owner Registration**  
  On startup, the connector registers its element name as an *External Owner* within the ticketing application so users can explicitly assign tickets to the connector.

- **Automatic Ticket Creation in ServiceNow**  
  Tickets created in the local system (and assigned to the connector) are automatically sent to ServiceNow, which creates the incident record in ServiceNow.

- **ServiceNow-driven Updates**  
  When an incident is modified in ServiceNow (status changes, priority, etc.), the connector pulls those updates and applies them to the corresponding DataMiner ticket.

- **Alarm Property Synchronization**  
 To ensure that incident details are correctly reflected in alarms, make sure the following properties exist:
  - `Incident Status`  
  - `Incident Number`
  - `Ticket ID`

## Limitations & Notes

- The connector **does not** allow DataMiner to overwrite ServiceNow incident data after creation; ServiceNow is the authoritative source for updates.
- If you need bidirectional updates (allowing local changes to update ServiceNow), this would require changes to the integration; contact the integration team to discuss options.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_ServiceNow_Incident_Manager_Technical).
