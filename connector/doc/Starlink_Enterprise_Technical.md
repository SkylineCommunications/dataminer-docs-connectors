---
uid: Connector_help_Starlink_Enterprise_Technical
---

# Starlink Enterprise

The purpose of this connector is to monitor Starlink devices through the Telemetry API and the Management API over HTTP using JSON files.

Starlink is an internet service that uses a satellite constellation in a low Earth orbit to deliver high-speed low-latency broadband internet. Because Starlink satellites are in a low orbit, at about 550 km from Earth, the round-trip data time between the user and a satellite is significantly lower compared to internet services that make use of single geostationary satellites.

The Starlink Telemetry API is a low-latency API for accessing the telemetry data from Starlink devices. This API is only available for enterprise accounts with an account manager. It is designed for users that have their own data infrastructure to monitor Starlink devices remotely. The API is stateless and will only respond with current telemetry data.

The Starlink Management API is used to activate, deactivate, and otherwise manage Starlink user terminals. Next to this, it can return paginated results containing data usage for the current and previous billing cycles for service lines on an account. Similar to the Telemetry API, this API is only available for enterprise accounts with an account manager.

The Starlink Enterprise connector was previously known as the Starlink Telemetry API connector. The name was changed to Starlink Enterprise when calls towards the Management API were added. The Starlink Enterprise 1.0.0.1 is the same connector as the Starlink Telemetry API 1.0.0.4. If you have any elements that are still using the Starlink Telemetry API, we recommend upgrading these to the latest version of the Starlink Enterprise connector.

> [!NOTE]
> **LEGAL NOTE**: This connector (or package) is intended solely for use in production with Skyline's usage-based services model. Any other use is prohibited. For more detailed information, see [Usage-based services](https://aka.dataminer.services/usage-based-services-docs). For inquiries regarding commercial production usage, contact Skyline Sales at <sales@skyline.be>.

> [!TIP]
> To optimize your use of this connector, we recommend deploying our **Standard Product Solution** [Starlink Enterprise](https://catalog.dataminer.services/details/66a4c259-0fb1-4c27-aede-8bbd3a4925d0) via the Catalog. This way, you will also be able to use the complementary low-code app and standard available dashboards.

## About

### Version Info

| Range              | Key Features    | Based on                       | System Impact |
|--------------------|-----------------|--------------------------------|---------------|
| 1.0.0.x [Obsolete] | Initial version | Starlink Telemetry API 1.0.0.4 | -             |
| 1.0.1.x [Obsolete] | Version with standardized foreign keys | Starlink Enterprise 1.0.0.16 | Foreign key parameters have been renamed, which impacts Automation scripts that retrieve a parameter of this protocol by name. |
| 1.0.2.x [Obsolete] | Telemetry Data is set using history sets for accurate backpolling. Partial table option implemented for large tables. | Starlink Enterprise 1.0.1.2 | Pagination for large tables (User Terminal, Services, Daily Data Usage, Monthly Data Usage, Overage Lines). History sets can cause alarm storms if hysteresis is not enabled on alarm templates. |
| 1.0.3.x [SLC Main] | Implemented multi-threading to poll management data and telemetry data on different threads. This will keep tables up to date with proper mapping of services and keep unconfigured terminals from persisting on tables. Updated display keys of User Terminal Table and Alerts Table to be unique using the device name and kit number | Starlink Enterprise 1.0.2.10  | Element needs to be reconfigured with a new connection using the Starlink API as the endpoint configured. Display keys changed on Alerts and User Terminal Tables.|

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | v1                 |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components                                                                            |
|---------|-----------------|---------------------|-------------------|----------------------------------------------------------------------------------------------- |
| 1.0.0.x | No              | Yes                 | -                 | [Starlink Enterprise - User Terminal](xref:Connector_help_Starlink_Enterprise_-_User_Terminal) |

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection to be able to interact with the API and requires the following input during element creation:

HTTP CONNECTION:

- **Type of port:** TCP/IP
- **IP address/host**: api.starlink.com

TCP/IP settings

- **IP port**: 443
- **Bus address**: *ByPassProxy*. This must be filled in to bypass any possible proxy that could block the HTTP communication.

#### HTTP Connection - Config Data

This connector uses a second HTTP connection thread to poll management data in parallel with telemetry data and requires the following input during element creation:

HTTP CONNECTION:

- **Type of port:** TCP/IP
- **IP address/host**: api.starlink.com

TCP/IP settings

- **IP port**: 443
- **Bus address**: *ByPassProxy*. This must be filled in to bypass any possible proxy that could block the HTTP communication.

### Initialization

A newly created element will only start polling data when both the **Client ID** and **Client Secret** are filled in on the **Configuration** page.

It is possible to install the Starlink Enterprise connector using the **Starlink Enterprise** application package, which provides a **simulation extension**. The simulation extension is installed alongside the application package. Upon installation, the simulation becomes available and utilizes built-in logic based on mock accounts and user terminals to replicate real-world scenarios. The simulation is enabled during the creation of the element. Simulation files are stored within the application's designated directory. History simulation data was added for the demo terminal "Skyline demo cruise_UT*74d101" to allow location tracking.

In case you make use of this package, the **simulation will run until you enter the Client ID and Client Secret** on the **Configuration** page. After that, the simulation stops, and the element begins polling data with real values from the device if the credentials are valid.

> [!IMPORTANT]
> No information will be polled by default. To enable polling, go to the **Accounts** table on the **Accounts** page, and use the toggle button of the relevant row(s) in the **Polling** column.

## How to Use

The connector uses JSON over HTTP to retrieve its data.

To see the actual traffic between the element and the device, a built-in DataMiner tool called Stream Viewer can be used. You can access it by right-clicking the element in the Surveyor and selecting **View** > **Stream Viewer**. A healthy element will show groups 700-705 in the Stream Viewer.

If you only see group 700 in the Stream Viewer, check the **Authentication** parameter and re-enter the client ID and client secret if the authentication failed.

If you only see groups 700 and 701 in the Stream Viewer, check the **Polling** column of the **Accounts** table, as probably none of the toggle buttons will be set to enabled.

Unexpected column names and user terminal alerts will be logged in the element log file. If you encounter these, please contact Skyline so that the connector can be corrected or extended. You can open the element log file by right-clicking the element in the Surveyor and selecting **View** > **Log**. However, note that lines in the element log file indicating *token_expired* can be safely ignored, as these are also added when nothing is wrong with the element.

> [!NOTE]
> Keep in mind that the tables User Terminals, Alerts, Routers, Services, Overage Lines, and Monthly and Daily Data Usage can be empty even if polling is enabled for at least one account, the Authentication parameter indicates *Successful*, and groups 700-705 are shown in the Stream Viewer.

> [!TIP]
> In case you notice that a large number of user terminals are not shown in the User Terminals table, restart the element. This will trigger a new access token request and a new poll cycle.

### User Terminals Page

The User Terminals page contains the **User Terminals** table. This table shows the Starlink terminals that are linked to the accounts for which polling is enabled.

The columns **Device ID**, **Account Number**, and **Service Line Number** in this table are hidden by default. You can show them by right-clicking the table column header, selecting **Columns**, and then selecting the columns you want to show.

As the Telemetry API does not always return the user terminals consistently, the connector will keep the terminals that are no longer returned by the API in the table for maximum one day. When the **Info Logging Level** of the element log file is raised to *Level 1* or higher, you will see a line in the log file when one or more terminals are still in the table but were not returned by the API.

Terminals that are no longer returned by the API for more than one day will be removed from the table. This action can also be logged in the element log file. The **Timestamp** column is used to determine the latest timestamp of when a row was updated.

User terminals for which the Timestamp column shows **N/A** are returned by the Management API and not by the Telemetry API. This means no telemetry (Signal Quality, Downlink Throughput, etc.) can be shown for these.

The **Device Name** column will show the service nickname if a service is active on the user terminal. The device ID is used as device name if no service is active. Changing the device name from the User Terminals table is currently not possible. To change it, you will need to use the Starlink web interface instead. The new name will then appear in the table after the next poll cycle.

The **Latitude** and **Longitude** combination represents a coordinate near the user terminal, but this is not the exact location. The longitude is calculated based on the H3 cell that is returned by the API (H3 geospatial indexing system). This H3 cell ID represents the center point of a hexagonal area, not the exact coordinates of a specific location within that area. If the exact location of the terminal is somewhere else within the hexagon, the latitude and longitude will differ.

When the **Info Logging Level** of the element log file is raised to *Level 1* or higher, you will see a line in the log file when no terminals are assigned to a specific account.

#### User Terminal DVEs

User terminals can be converted to dynamic virtual elements (DVEs). To **generate a DVE**, enable the **DVE Creation** toggle button for a specific terminal in the **User Terminals** table.

To **remove a DVE**:

1. Make sure that the **DVE Creation** toggle button for the corresponding terminal is set to *Disabled* in the **User Terminals** table.
1. Navigate to the **User Terminal DVEs Configuration** page via the page button on the **Configuration** page or by clicking the downwards arrow next to Configuration.
1. Click the **Delete** button for the corresponding terminal.
1. Read the warning message carefully.
1. If you are sure that the DVE can be removed, click **Yes** to confirm.

User terminal DVEs can only be removed if the DVE Creation column contains a value other than *Enabled*. User terminals for which a dynamic virtual element was created will not be removed automatically if they are no longer returned by the API for more than one day and have DVE Creation set to *Enabled*.

#### Relations to other tables

The data retrieved and stored in the different tables can be linked to each other. For the hardware-related information, this is with the column **User Terminal Device ID**, while for the more service-related data, the **Service Line Number** is used.

![Relations between tables](~/connector/images/Starlink_Enterprise_UserTerminalsRelationships.drawio.svg)

### Alerts Page

Each row in the **Alerts** table represents an alert that comes from a user terminal (not from a router). Alerts will persist for as long as they are active.

The **User Terminal Device ID** column in this table is hidden by default. You can show it by right-clicking the table column header, selecting **Columns**, and then selecting this column.

### Routers Page

Information related to routers is stored in the **Routers** table.

The **Account Number** column in this table is hidden by default. You can show it by right-clicking the table column header, selecting **Columns**, and then selecting this column.

As the Telemetry API does not always return the routers consistently, the connector will keep the routers that are no longer returned by the API in the table for at most one day. When the **Info Logging Level** of the element log file is raised to *Level 1* or higher, you will see a line in the log file when one or more routers are still in the table but were not returned by the API.

Routers that are no longer returned by the API for more than one day will be removed from the table. This action can also be logged in the element log file. The **Timestamp** column is used to determine the latest timestamp of when a row was updated.

The **User Terminal Device ID** column contains the reference to the Device ID of the user terminal. In the API, this is referred to as the **Router Dish ID**.

### IP Allocations Page

Information related to IP allocations is stored in the **IP Allocations** table.

The **IP Allocation Device ID** column in this table is hidden by default. You can show it by right-clicking the table column header, selecting **Columns**, and then selecting this column.

The **User Terminal Device ID** column contains the reference to the device ID of the user terminal.

### Services Page

The rows in the **Services** table represent the active service plans of the accounts.

The **Account Number** column in this table is hidden by default. You can show it by right-clicking the table column header, selecting **Columns**, and then selecting this column.

When the **Info Logging Level** of the element log file is raised to *Level 1* or higher, you will see a line in the log file when no services are active for a specific account.

### Overage Lines Page

This table shows the overages, which are additional services or data consumed beyond the limit.

The **Service** column in the Overage Lines table is hidden by default. You can show it by right-clicking the table column header, selecting **Columns**, and then selecting this column.

### Monthly Data Usage Page

On this page, you can review and monitor your data usage per month by type of data consumed (*Fixed* or *Mobile*, *Priority* or *Standard*).

The **Service** column in the **Monthly Data Usage** table is hidden by default. You can show it by right-clicking the table column header, selecting **Columns**, and then selecting this column.

The data in the Monthly Data Usage table is retained for 12 months.

### Daily Data Usage Page

On this page, you can review and monitor your data usage per day by type of data consumed (*Fixed* or *Mobile*, *Priority* or *Standard*).

The **Service** column in the **Daily Data Usage** table is hidden by default. You can show it by right-clicking the table column header, selecting **Columns**, and then selecting this column.

### Accounts Page

All known accounts are listed in the Accounts table. Each row in this table contains a polling toggle button. No information will be polled by default. The toggle button of every row will indicate *Disabled* after element creation. You will need to enable polling for the relevant accounts to be able to see data in the following tables: User Terminals, Alerts, Routers, Services, Overage Lines, and Monthly and Daily Data Usage.

> [!NOTE]
> Keep in mind that after you enable polling for one or more accounts, it can take some time before data is visible in the tables User Terminals, Alerts, Routers, Services, Overage Lines, and Monthly and Daily Data Usage. There is no trigger after changing one or more toggle buttons. Every timer cycle, the connector checks for which accounts polling is enabled.

### Configuration Page

The Configuration page contains the **Client ID**, the **Client Secret**, and the **Authentication** field. When the specified client ID and client secret have both been accepted by the API, the Authentication field will indicate *Successful*, and the element will start to display data. The connector will update its access token every 15 minutes, just before it expires.

In case the element **does not show any data**, and traffic inside the Stream Viewer seems minimal, check if the Authentication parameter indicates *Successful*. If it instead indicates *Failed*, most likely the client ID or the client secret is not correct.

The polling mechanism is triggered after the value of the Client Secret parameter changes. This means that a Client Secret value change is required to trigger a new poll cycle after an incorrect Client ID is corrected.

> [!CAUTION]
> Changing the client secret will also remove all dynamic virtual elements.

The Configuration page also contains two telemetry request configuration parameters:

- **Telemetry Batch Size** represents the maximum number of telemetry entries to return in the response. The recommended batch size is ~65000 records per request (this is the maximum). If the batch does not have that size, it will return less. Keeping it at 65000 allows fast backpolling when needed.
- **Telemetry Linger Duration** represents the maximum number of milliseconds to collect telemetry entries. The recommended linger duration is ~15000 ms. This duration is recommended by Starlink in order for all the data points to come in accurately.

> [!NOTE]
>
> - Both the batch size and the linger duration are set to 100 by default to keep the load on the API as low as possible.
> - Telemetry is polled every minute; content is stored using history sets for accurate backpolling.

### User Terminal DVEs Configuration page

Every row in the **User Terminal DVEs** table represents a DVE.

If the table is empty, this means no DVEs have been generated yet.

When a user generates a DVE by enabling the **DVE Creation** toggle button in the **User Terminals** table, a new row will appear in this table.

Removing a DVE is only possibly via the **Delete** button in the **User Terminal DVEs** table. See [User Terminal DVEs](#user-terminal-dves).

