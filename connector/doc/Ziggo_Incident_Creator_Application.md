---
uid: Connector_help_Ziggo_Incident_Creator_Application
---

# Ziggo Incident Creator Application

Ticketing System for USMS tickets and trigger IVR.

This connector will automatically create tickets based on correlated alarms. It also allows the operator to manually create tickets on existing alarms and even close them. The connector will list all created tickets and update their status from RSS feeds.

USMS tickets are forwarded towards the Ziggo USMS Ticket Gateway connector and IVR is sent to Ziggo IVR Gateway connector.

## About

### Version Info

| Range              | Key Features                         | Based on | System Impact |
|--------------------|--------------------------------------|----------|---------------|
| 1.0.0.x [Obsolete] | Initial version                      | -        | -             |
| 1.0.1.x [SLC Main] | Connector is now Cassandra-compliant | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |
| 1.0.1.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | No                  | -                 | -                   |
| 1.0.1.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Configuration of Remote Elements

For each Gateway element, you need to configure the DMA ID and element ID on the **Remote Element Config** page.

### Configuration of RSS Feeds

On the **Ticket** page, the IP of the **RSS Feed Server** must be configured and an **RSS Refresh Time** must be set. This will update the **Ticket Table** with the info from the RRS feeds every x minutes. The **Resolved TTL** defines the time to live for each resolved ticket before it is deleted from the Ticket Table.

## How to Use

### Tickets

The **Ticket Table** shows an overview of all alarms and the associated created tickets. It also contains tickets from the RSS feed server (if configured).

**Tickets stats** provides an overview of all ticket info grouped by platform. The TOTAL row contains statistics for all platforms.

### Ticket Config

To import data from a file, configure an import file in the **Import Config Table** and use the **Import** button. To check the result of the import, click the **Imported** page button. This imported data is used for different selection boxes during the creation of templates and tickets.

### Template

If you create a new template, it will be added in the **Template** table. Existing templates can be edited or deleted. Every template has its own preconfigured settings, used during the creation of new tickets.

A template can have multiple linked tasks. These are available in the **Template Task Table**. To edit a task, you need to configure the corresponding template.

### Remote Element Config

This page allows the configuration of the remote Gateway connectors (see [Configuration of Remote Elements](#configuration-of-remote-elements)).

### Source Tables

This page displays the tables used to build the tree control on the **Tree Control Overview** page.

Apart from the Time Window Table, the tables are filled in automatically. For the **Time Window Table**, you can use the **Add** button on the **Tree Control Overview** page. You will then need to set the start and end time for the time window, the severity and the platform.

The **Platform** table is filled in with values found in the element properties (Platform Dashboard).

Note: for the **Start Time** and **End Time**, only the hour and minute matter. However, it is important to also choose a day for the Start Time, so that the **Day of the Week** can be filled in accordingly.

### Tree Control Overview

This tree control follows this hierarchy (4 tables and relations between them):

1. Platform (detected from list of values in element property).
1. Severity (4 levels: warning, minor, major, critical).
1. Day of the week (7 days: Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, Sunday).
1. Time window: One or more time windows during which auto-ticketing is allowed (in the format hh:mm-hh:mm).

### Close Incident Overview

- Index
- Incident ID
- DMA/Alarm ID
- Added On
- State
- Traffic State
- Retries
- Last GUID
- Last Updated

#### Closing Configuration

You can enable **Detailed Logging** on the **Create and Close Config** page. If this setting is enabled, the connector will provide you with all information of the flow of the connector in the logging of the element. If you disable this toggle button, only errors will be logged.

## Notes

For the creation of tickets and the configuration of templates, a custom Visio file and IAS is required.
