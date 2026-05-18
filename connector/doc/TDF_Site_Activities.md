---
uid: Connector_help_TDF_Site_Activities
---

# TDF Site Activities

## About

The **TDF Site Activities** connector integrates with the ServiceNow REST API to provide real-time visibility into ticketing activities. It enables operators to monitor technician presence, incident tickets, maintenance planning, access requests, and site notes.

## Key Features

- **Technician Presence on Site**: View technician on-site presence with timestamps and details.
- **Incident Tickets**: Monitor active and historical incident tickets with impact assessment.
- **Plan Maintenance Tickets**: Track scheduled maintenance activities.
- **Technician Move on Site**: Follow technician deployment requests.
- **Access Requests**: Monitor site access requests for the current day.
- **Site Notes**: Display operational notes attached to sites.
- **Site Incident Overview**: Aggregated incident counts per site.
- **Polling Manager**: Configurable polling intervals for each data set.

## Use Case

**Challenge**: Site operators lack a unified view of ticketing activities across multiple TDF sites, requiring repeated logins to ServiceNow to check technician availability, ongoing incidents, and maintenance schedules.

**Solution**: The connector polls ServiceNow tables and displays technician presence, incidents, maintenance tickets, access requests, and site notes in dedicated DataMiner pages with configurable polling intervals.

**Benefit**: Operators get a real-time overview of all site activities in one place, enabling faster decision-making and reducing manual checks.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_TDF_Site_Activities_Technical).
