---
uid: Connector_help_Observium_Network_Platform_Technical
---

# Observium Network Platform

## About

Observium is a network monitoring platform with auto-discovery that supports a wide range of device types, vendors, and operating systems. This connector polls the Observium REST API to retrieve the discovered device inventory and to monitor the availability of the Observium platform itself.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the Observium web server.
- **IP port**: The IP port of the Observium web server.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

### Initialization

After element creation, configure the authentication on the **Configuration** page:

1. Select the desired **Authentication Mode**:

   - *Username + Password*: HTTP Basic authentication with an Observium user account.
   - *API Token*: Authentication with an Observium API token, sent in a dedicated HTTP header.

2. Enter the credentials corresponding to the selected mode.

Polling will fail with a clear status message as long as no credentials are configured for the selected authentication mode.

## How to Use

The connector retrieves data by polling the Observium REST API (`/api/v0`) over HTTP(S). The Observium API does not support push notifications, so all data is polled; data freshness is bounded by the configured polling intervals.

The **General** page shows the **API Connection State** (the result of the most recent API request, monitored), the **Device Count**, and the **Devices Overview** table with one row per device known to Observium (display key: hostname).

Polling is controlled through the **Polling Manager**, available via a page button on the **Configuration** page. Each poll type has a row with its **State** (Enabled/Disabled), **Interval**, **Last Poll** timestamp, **Status**, and **Details**. Polls can also be triggered on demand with the **Poll** button, including on disabled rows, allowing manual override.

## Notes

When switching authentication modes on a running element, the Observium server can briefly keep the previous session alive through its session cookie. The connector guards against polling with unconfigured credentials, but a previously established server session may remain valid until it expires on the server side.
