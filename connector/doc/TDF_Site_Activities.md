---
uid: Connector_help_TDF_Site_Activities
---

# TDF Site Activities

## About

The TDF Site Activities connector integrates with the ServiceNow REST API to provide real-time visibility into ticketing activities. It enables operators to monitor technician presence, incident tickets, maintenance planning, access requests, and site notes.

## Key Features

- **Technician presence on site**: View technician on-site presence with timestamps and details.
- **Incident tickets**: Monitor active and historical incident tickets with impact assessment.
- **Plan maintenance tickets**: Track scheduled maintenance activities.
- **Technician move on site**: Follow technician deployment requests.
- **Access requests**: Monitor site access requests for the current day.
- **Site notes**: Display operational notes attached to sites.
- **Site incident overview**: View aggregated incident counts per site.
- **Polling manager**: Fine-tune polling intervals for each data set.

## Use Case

**Challenge**: Site operators lack a unified view of ticketing activities across multiple TDF sites, requiring repeated logins to ServiceNow to check technician availability, ongoing incidents, and maintenance schedules.

**Solution**: The connector polls ServiceNow tables and displays technician presence, incidents, maintenance tickets, access requests, and site notes on dedicated DataMiner pages with configurable polling intervals.

**Benefit**: Operators get a real-time overview of all site activities in one place, enabling faster decision-making and reducing manual checks.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_TDF_Site_Activities_Technical).
