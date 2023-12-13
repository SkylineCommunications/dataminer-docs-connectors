---
uid: Connector_help_Starlink_Telemetry_API
---

# Starlink Telemetry API

The purpose of this connector is to monitor Starlink devices through the Telemetry API over HTTP using JSON files.

Starlink is an internet service that uses a satellite constellation in a low Earth orbit to deliver high-speed low-latency broadband internet. Because Starlink satellites are in a low orbit, at about 550 km from Earth, the round-trip data time between the user and a satellite is significantly lower compared to internet services that make use of single geostationary satellites.

The Starlink Telemetry API is a low-latency API for accessing the telemetry data from Starlink devices. It is designed for users that have their own data infrastructure to monitor Starlink devices remotely. The Telemetry API is a stateless API that will only respond with current telemetry data.

## About

### Version Info

| Range              | Key Features    | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | TBD                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection to be able to interact with the Telemetry API and requires the following input during element creation:

HTTP CONNECTION:

- **Type of port:** TCP/IP
- **IP address/host**: api.starlink.com

TCP/IP settings

- **IP port**: 443
- **Bus address**: *ByPassProxy*. This must be filled in to bypass any possible proxy that could block the HTTP communication.

### Initialization

A newly created element will only start polling data when both the **Client ID** and **Client Secret** are filled in on the **Configuration** page.

> [!IMPORTANT]
> No telemetry will be polled by default. To enable telemetry polling, go to the **Accounts** table on the **Accounts** page, and use the toggle button of the relevant row(s) in the **Polling** column.

### Redundancy

No redundancy is defined in the connector.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector uses JSON over HTTP to retrieve its data.

To see the actual traffic between the element and the device, a built-in DataMiner tool called Stream Viewer can be used. You can access it by right-clicking the element in the Surveyor and selecting **View** > **Stream Viewer**. A healthy element will show groups 700-702 in the Stream Viewer.

If you only see group 700 in the Stream Viewer, check the **Authentication** parameter and re-enter the client ID and client secret if the authentication failed.

If you only see groups 700 and 701 in the Stream Viewer, check the **Polling** column of the **Accounts** table, as probably none of the toggle buttons will be set to enabled.

Unexpected column names and user terminal alerts will be logged in the element log file. If you encounter these, please contact Skyline so that the connector can be corrected or extended. You can open the element log file by right-clicking the element in the Surveyor and selecting **View** > **Log**.

> [!NOTE]
> Keep in mind that the tables User Terminals, Alerts, and Routers can be empty even if polling is enabled for at least one account, the Authentication parameter indicates *Successful*, and groups 700-702 are shown in the Stream Viewer.

> [!TIP]
> In case you notice that a large number of user terminals are not shown in the User Terminals table, restart the element. This will trigger a new access token request and a new poll cycle.

### User Terminals Page

The User Terminals page contains the **User Terminals** table. This table shows the Starlink terminals that are linked to the accounts for which polling is enabled.

The columns **Device ID** and **Account Number** in this table are hidden by default. You can show them by right-clicking the table column header, selecting **Columns**, and then selecting the columns you want to show.

As the Telemetry API does not always return the user terminals consistently, the terminals that are no longer returned by the API will be kept in the table for one day at most. You will see a line in the element log file when one or more terminals are still in the table but were not returned by the API.

Terminals that are no longer returned by the API for more than one day will be removed from the table. This action will also be logged in the element log file. The **Timestamp** column is used to determine the latest timestamp of when a row was updated.

You can assign a name to each user terminal in the **Device Name** column. These names will only be used by DataMiner and will not be communicated to the API. Keep in mind that a name will not be accepted if it contains invalid symbols.

### Alerts Page

Each row in the **Alerts** table represents an alert that comes from a user terminal (not from a router). Alerts will persist for as long as they are active.

### Routers Page

Information related to routers is stored in the **Routers** table.

The **Account Number** column in this table is hidden by default. You can show it by right-clicking the table column header, selecting **Columns**, and then selecting this column.

### Accounts Page

All known accounts are listed in the Accounts table. Each row in this table contains a polling toggle button. No telemetry will be polled by default. The toggle button of every row will indicate *Disabled* after element creation. You will need to enable polling for the relevant accounts to be able to see data in the following tables: User Terminals, Alerts, and Routers.

> [!NOTE]
> Keep in mind that after you enable polling for one or more accounts, it can take some time before data is visible in the tables User Terminals, Alerts, and Routers. There is no trigger after changing one or more toggle buttons. Every timer cycle, the connector checks for which accounts polling is enabled.

### Configuration Page

The Configuration page contains the **Client ID**, the **Client Secret**, and the **Authentication** field. When the specified client ID and client secret have both been accepted by the API, the Authentication field will indicate *Successful*, and the element will start to display data. The connector will update its access token every 15 minutes, just before it expires.

In case the element **does not show any data**, and traffic inside the Stream Viewer seems minimal, check if the Authentication parameter indicates *Successful*. If it instead indicates *Failed*, most likely the client ID or the client secret is not correct.

The polling mechanism is triggered after the value of the Client Secret parameter changes. This means that a Client Secret value change is required to trigger a new poll cycle after an incorrect Client ID is corrected.

The Configuration page also contains two telemetry request configuration parameters:

- **Telemetry Batch Size** represents the maximum number of telemetry entries to return in the response. The recommended batch size is ~1000 records per request.
- **Telemetry Linger Duration** represents the maximum number of milliseconds to collect telemetry entries. The recommended linger duration is ~1000 ms.

> [!NOTE]
> Both the batch size and the linger duration are set to 100 by default to keep the load on the API as low as possible.
