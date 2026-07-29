---
uid: Connector_help_Observium_Network_Platform_Technical
---

# Observium Network Platform

## About

Observium is a network monitoring platform with auto-discovery that supports a wide range of device types, vendors, and operating systems. This connector polls the Observium REST API to retrieve the discovered device inventory and to monitor the availability of the Observium platform itself.

> [!IMPORTANT]
> The Observium REST API is only included in the paid Subscription Editions (Professional or Enterprise) of Observium. The free Community Edition does not include the REST API and can therefore not be integrated with this connector.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the Observium web server. When the Observium server is only reachable over HTTPS, prefix the address with *https://*.
- **IP port**: The IP port of the Observium web server. The default is *80*; for HTTPS, this is typically *443*.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*. This is the default value.

### Initialization

After element creation, configure the authentication on the **Configuration** page:

1. Select the desired **Authentication Mode**:

   - *Username + Password*: HTTP Basic authentication with an Observium user account.
   - *API Token*: Authentication with an Observium API token, sent in the standard *Authorization* HTTP header (Bearer scheme).

2. Enter the credentials corresponding to the selected mode.

To retrieve the complete device inventory, the configured account (or the account backing the API token) needs at least Observium user level 5 (*Global Read*). Accounts with a lower level will only return the devices explicitly permitted to them.

Polling will fail with a clear status message as long as no credentials are configured for the selected authentication mode.

## How to Use

The connector retrieves data by polling the Observium REST API (`/api/v0`) over HTTP(S). The Observium API does not support push notifications, so all data is polled; data freshness is bounded by the configured polling intervals.

The **General** page shows the **Device Count**, i.e. the total number of devices reported by the Observium API.

The **Devices** page shows the **Device Count** and the **Devices Overview** table, with one row per device known to Observium (display key: hostname).

The **Configuration** page shows the **API Connection State**, reflecting the result of the most recent API request. This parameter is monitored and raises an alarm by default when communication with the Observium server fails. Note that the connection state is only refreshed when a poll runs, so the detection time is bounded by the configured polling interval.

Polling is controlled through the **Polling Manager**, available via a page button on the **Configuration** page. Each poll type has a row with its **State** (Enabled/Disabled), **Last Poll** timestamp, **Interval**, **Status**, and **Details**. Polls can also be triggered on demand with the **Poll** button, including on disabled rows, allowing manual override.

By default, the *Devices* poll is enabled with an interval of 1 day. The interval can be configured between 5 seconds and 7 days, in steps of 5 seconds.

## Notes

When switching authentication modes on a running element, the Observium server can briefly keep the previous session alive through its session cookie. The connector guards against polling with unconfigured credentials, but a previously established server session may remain valid until it expires on the server side.
