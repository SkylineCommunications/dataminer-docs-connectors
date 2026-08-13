---
uid: Connector_help_Telenet_B2B_Inventory_Manager
---

# Telenet B2B Inventory Manager

The Telenet B2B Inventory Manager connector retrieves CPE and mobile modem inventory from Telenet's REST APIs and keeps that inventory available in DataMiner. It also forwards the resulting ping destinations to a Generic Ping element via InterApp, so that reachability monitoring can be set up on top of the inventory data.

## About

### Version Info

| Range              | Key Features                                                                          | Based on | System Impact  |
|--------------------|---------------------------------------------------------------------------------------|----------|----------------|
| 1.0.0.x [SLC Main] | Initial version: CPE and modem inventory polling, InterApp forwarding to Generic Ping | -        | -              |

### Product Info

| Range   | Supported System            |
|---------|-----------------------------|
| 1.0.0.x | Telenet CPE and mobile modem inventory REST APIs |

### System Info

| Range   | DCF Integration  | Cassandra Compliant  | Linked Components           | Exported Components |
|---------|------------------|----------------------|-----------------------------|---------------------|
| 1.0.0.x | No               | Yes                  | Generic Ping (via InterApp) | -                   |

## Configuration

### Connections

#### HTTP Connection - CPE

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The base URL of the CPE inventory API, e.g., `normapi.prd.inet.telenet.be` (production) or `normapi-test.prd.inet.telenet.be` (test).
- **IP port**: The IP port of the CPE inventory API, e.g., `8123` (production) or `9123` (test).
- **Device address**: The device address used to route the connection (default: ByPassProxy).

#### HTTP Connection - Modem

This connector uses a second, independent HTTP connection for the mobile modem inventory API and requires the following input during element creation:

- **IP address/host**: The base URL of the modem inventory API.
- **IP port**: The IP port of the modem inventory API.

### Initialization

After element creation, the following parameters must be configured before polling can succeed:

- **CPE API Key**: The `x-api-key` value sent on every request to the CPE inventory endpoint.
- **Ping Element Name**: The name of the Generic Ping element that inventory updates should be forwarded to.
- **JSON Path parameters** (CPE and modem, 5 per type): JSONPath expressions that extract the values to populate the Property 1-5 columns from each inventory item. Changing a JSON path triggers an immediate re-poll of the corresponding endpoint so the table reflects the new value without waiting for the next scheduled cycle.

## How to use

InterApp messages are used to forward inventory changes to the linked Generic Ping element; no related traffic will be visible in the Stream Viewer for that part of the flow, since it does not go over the polled HTTP connections. Only the CPE and modem HTTP requests/responses are visible in the Stream Viewer.

### General

You can find the following parameters on this page:

- **CPE API Key**: The authentication key used for CPE inventory requests.
- **CPE Poll HTTP Status** / **Modem Poll HTTP Status**: The HTTP status line of the last poll for each endpoint.
- **CPE Poll Last Update** / **Modem Poll Last Update**: Timestamp of the last successful poll for each endpoint.
- **Ping Element Name**: The configured Generic Ping element that receives inventory updates.

### CPE

- The **CPE** table lists all CPE devices returned by the inventory API, keyed by IP address. Each row shows the hostname and up to five configurable properties, populated using the JSON path parameters on the CPE Configuration page.

### Modem

- The **Modem** table lists all mobile modems returned by the inventory API, keyed by serial number. The hostname column is derived by appending `.acsmd.telenet-ops.be` to the modem's serial number, since the source API does not provide a hostname directly. The table also shows device type and up to five configurable properties.

### CPE Configuration / Modem Configuration

- The **JSON Path 1-5** parameters on these pages define which fields are extracted from each CPE or modem inventory item into the Property 1-5 columns of the corresponding table. A JSON path can point to a top-level field or a nested field in the response.

## Notes

Ping destinations are only forwarded to the Generic Ping element for entries that are new or whose relevant field values changed since the last poll; unchanged entries are not resent. Entries no longer present in an inventory response are reported as deletions to the linked Generic Ping element.