---
uid: Connector_help_Telenet_B2B_Inventory_Manager_Technical
---

# Telenet B2B Inventory Manager

## About

The Telenet B2B Inventory Manager connector polls CPE and cable modem inventory from Telenet's B2B inventory APIs and keeps a live view of both estates in DataMiner. It also automatically distributes each polled CPE and modem address to a configured Generic Ping element, so that connectivity monitoring for the full estate can be spread across multiple ping elements without any address ever being monitored by more than one element at a time.

## Configuration

### Connections

This connector uses two HTTP connections:

#### HTTP Connection - CPE (default connection)

Used to poll the CPE inventory endpoint. Requires the following input during element creation:

- **IP address/host**: The host of the CPE inventory API.
- **IP port**: The IP port of the CPE inventory API (default: *9123*).

Requests to this endpoint are authenticated using the **CPE API Key** parameter, sent as the `x-api-key` header.

#### HTTP Connection - Modem (advanced connection)

Used to poll the modem inventory endpoint. Requires its own host/port to be configured during element creation, separate from the CPE connection above.

### CPE/Modem property mapping

On the **CPE Configuration** and **Modem Configuration** pages, you can configure up to 5 JSONPath expressions per inventory type (**CPE JSON Path 1-5** / **Modem JSON Path 1-5**). Each expression is applied to every item in the corresponding inventory API response to populate the **Property 1-5** columns of the **CPE**/**Modem** table.

### Ping Configuration

Each of the **CPE Configuration** and **Modem Configuration** pages contains its own **Ping Configuration** table, listing the Generic Ping elements that CPE (respectively modem) addresses are distributed to. A Generic Ping element can only be configured for one of the two tables at a time; the connector refuses to add the same element to both.

Underneath each table, a context menu provides the following actions:

- **Add element...**: Adds the Generic Ping element name entered in the input field to the table.
- **Delete selected element(s)...**: Removes the selected element(s) from the table. Any addresses that were assigned to a removed element are automatically reassigned to one of the remaining configured elements on the next poll.
- **Redistribute pings...**: Manually rebalances all currently assigned addresses evenly across the configured elements. This requires at least 2 elements to be configured, and all of them to be active; otherwise the action is refused.

#### Address-to-element assignment behavior

Every polled CPE and modem address is assigned to exactly one Generic Ping element:

- **New addresses** (never seen before, or whose previous element is no longer configured) are automatically assigned to whichever configured element currently has the fewest assigned addresses.
- **Existing addresses** whose assigned element is still configured are never automatically moved to a different element, even if a new element is added to the table afterwards. They keep being sent to the same element as long as it remains configured and active.
- Addresses are only ever rebalanced across elements through the **Redistribute pings...** action described above, guaranteeing that no address is ever pinged from two different elements at the same time (outside of the brief transition window during an active redistribution).

## How to use

### General

This page shows the **CPE API Key** used to authenticate CPE inventory requests, as well as the HTTP status code and timestamp of the last successful poll for both the CPE and Modem inventory.

### CPE

This page contains the **CPE** table with all polled CPE endpoints, showing the CPE's IP address, hostname, and the 5 configurable properties extracted from the API response. A page button links to the **CPE Configuration** page.

### Modem

This page contains the **Modem** table with all polled cable modem endpoints, showing the modem's serial number, hostname, device type, and the 5 configurable properties extracted from the API response. A page button links to the **Modem Configuration** page.

### CPE Configuration / Modem Configuration

These pages allow you to configure the JSONPath expressions used to populate the **Property 1-5** columns of the corresponding table, as well as the **Ping Configuration** table and its **Add element...**/**Delete selected element(s)...**/**Redistribute pings...** actions described above.