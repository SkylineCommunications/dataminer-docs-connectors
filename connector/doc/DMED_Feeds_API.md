---
uid: Connector_help_DMED_Feeds_API
---

# DMED Feeds API

## About

The **DMED Feeds API** connector brings DMED feed bookings into DataMiner. It retrieves each feed's name, schedule, facility, source, destination, assigned ITXR, and status from the DMED Feeds API and presents them in one place, together with a history of past feeds.

The connector can be limited to the facilities and device types you care about, so that only relevant feeds are shown.

## Key Features

- **Live feed overview**: See current and upcoming feeds with their start, end, on and off times, facility, source, destination, and status (*Open*, *Provisioned*, *Built*, *Cleared*, or *Goodnight*).

- **Feed history**: Review previously delivered feeds, loaded automatically when the element starts, to support follow-up and post-event analysis.

- **Targeted view**: Filter by destination facility and device type, and choose how far back and ahead feeds are retrieved, so operators only see what is relevant to them.

- **Health visibility**: Monitor whether the connection to the Feeds API is healthy, how many feeds were retrieved, and when the last update took place. An alarm is raised when the connection fails.

## Use Cases

### Operational awareness of scheduled feeds

**Challenge**: Operators need to know which feeds are scheduled, where they come from, and where they go, without logging in to a separate booking system.

**Solution**: The connector continuously refreshes the list of feeds in DataMiner, including their schedule and status.

**Benefit**: Operations teams get a single, always up-to-date view of feed activity alongside the rest of their monitored infrastructure.

### Facility-focused monitoring

**Challenge**: A specific facility or team only cares about the feeds that concern its own destinations and equipment.

**Solution**: Filter the retrieved feeds by destination facility and device type.

**Benefit**: Less noise and a focused view tailored to each facility or team.

### Post-event review

**Challenge**: After an event, teams need to check which feeds were booked, when, and between which locations.

**Solution**: The connector keeps a history of past feeds for the configured period.

**Benefit**: Quick answers when investigating incidents or validating past bookings.

## Technical Reference

### Prerequisites

- **A DMED Feeds API account** is needed for the connector to authenticate. A user name and password are entered after the element is created.

- **Network access to the Feeds API over HTTPS** is required from the DataMiner Agent.

- **DataMiner 10.4.0 (14003) or higher** is required.


> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_DMED_Feeds_API_Technical).