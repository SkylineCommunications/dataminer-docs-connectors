---
uid: Connector_help_DMED_Feeds_API_Technical
---

# DMED Feeds API

## About

The **DMED Feeds API** connector retrieves feeds from the DMED Feeds API and keeps them up to date in DataMiner. For each feed, it provides the name, start and end time, on and off time, facility, source, destination, assigned ITXR, LOC code, and status (*Open*, *Provisioned*, *Built*, *Cleared*, or *Goodnight*).

Feeds that have ended or been cleared are moved from the **Feeds** table to the **Feed History** table, so that recent past feeds remain available for review.

## Configuration

### Connections

#### HTTP Connection - Search Feeds

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The IP address or URL of the Feeds API.
- **IP port**: The IP port of the destination (default: *443*).
- **Bus address**: *ByPassProxy* (to bypass the proxy server).

### Initialization

After the element is created, go to the **Configuration** page and enter the **User Name** and **Password** used for Basic authentication on the Feeds API. Optionally, adjust the filters and time windows described below.

## How to Use

The connector polls the Feeds API periodically. No manual action is needed after the credentials are configured.

### Configuration

On the **Configuration** page, you can set the following:

- **User Name** and **Password**: The credentials used to authenticate on the Feeds API. The password is masked.
- **Facility Filter**: A semicolon-separated list of destination facility descriptions to include (e.g., *Bristol (ESPN)*). Default: *\**, which includes all facilities.
- **Device Type Filter**: A semicolon-separated list of destination device types to include. Default: *ASIS*. Use *\** to include all.
- **Poll Interval**: The time between two polls of the Feeds API, in minutes (default: *1*).
- **Past Feed Window**: How far back in time feeds are retrieved, in hours. This also determine how long a feed last in the Feeds table before being moved to Feeds History table. (default: *24*).
- **Future Feed Window**: How far ahead in time feeds are retrieved, in hours (default: *24*).
- **Feed History Time**: How far back feed history is loaded at startup, in hours (default: *168*). History older than this is removed.
