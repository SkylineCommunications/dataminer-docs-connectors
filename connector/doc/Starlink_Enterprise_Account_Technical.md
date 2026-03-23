---
uid: Connector_help_Starlink_Enterprise_Account_Technical
---

# Starlink Enterprise Account

## About

The purpose of this connector is to poll Starlink devices through the Telemetry API and the Management API over HTTP using JSON files. The polled information gets offloaded to an element which was created based on the [Starlink Enterprise connector](https://catalog.dataminer.services/details/d1dc1fae-0902-4cc3-9ae6-d1983d9596a3).

Starlink is an internet service that uses a satellite constellation in a low Earth orbit to deliver high-speed low-latency broadband internet. Because Starlink satellites are in a low orbit, at about 550 km from Earth, the round-trip data time between the user and a satellite is significantly lower compared to internet services that make use of single geostationary satellites.

The Starlink Telemetry API is a low-latency API for accessing the telemetry data from Starlink devices. This API is only available for enterprise accounts with an account manager. It is designed for users that have their own data infrastructure to monitor Starlink devices remotely. The API is stateless and will only respond with current telemetry data.

The Starlink Management API is used to activate, deactivate, and otherwise manage Starlink user terminals. Next to this, it can return paginated results containing data usage for the current and previous billing cycles for service lines on an account. Similar to the Telemetry API, this API is only available for enterprise accounts with an account manager.

Elements that are created based on this connector don't show anything. The connector was designed for querying the Starlink API V2 only. A [Starlink Enterprise element](https://catalog.dataminer.services/details/d1dc1fae-0902-4cc3-9ae6-d1983d9596a3) with name **Starlink Enterprise** is required to make the polled information visible, alarmable and trendable.

Since the introduction of the Starlink API V2, credentials are required per account. These credentials have to be entered on the **General** page of a Starlink Enterprise Account element. The name of the Starlink Enterprise Account element has to match the **account name**.

> [!NOTE]
> **LEGAL NOTE**: This connector (or package) is intended solely for use in production with Skyline's usage-based services model. Any other use is prohibited. For more detailed information, see [Usage-based services](https://aka.dataminer.services/usage-based-services-docs). For inquiries regarding commercial production usage, contact Skyline Sales at <sales@skyline.be>.

> [!TIP]
> To optimize your use of this connector, we recommend deploying our **Standard Product Solution** [Starlink Enterprise](https://catalog.dataminer.services/details/66a4c259-0fb1-4c27-aede-8bbd3a4925d0) via the Catalog. This way, you will also be able to use the complementary low-code app and standard available dashboards.

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | API V2             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components                                               | Exported Components |
|---------|-----------------|---------------------|-----------------------------------------------------------------|-------------------- |
| 1.0.0.x | No              | Yes                 | [Starlink Enterprise ](xref:Connector_help_Starlink_Enterprise) | -                   |

## Configuration

### Connections

#### HTTP Connection - Telemetry API

This connector uses an HTTP connection to be able to interact with the API and requires the following input during element creation:

HTTP CONNECTION:

- **Type of port:** TCP/IP
- **IP address/host**: api.starlink.com

TCP/IP settings

- **IP port**: 443
- **Bus address**: *ByPassProxy*. This must be filled in to bypass any possible proxy that could block the HTTP communication.

> [!NOTE]
> Using *ByPassProxy* may result in `Error : 12002. ERROR_WINHTTP_TIMEOUT` if the server requires routing through a security-enforcing proxy. In such cases, remove the *ByPassProxy* entry from *Bus address* to restore connectivity.

#### HTTP Connection - Management API

This connector uses a second HTTP connection thread to poll management data in parallel with telemetry data and requires the following input during element creation:

HTTP CONNECTION:

- **Type of port:** TCP/IP
- **IP address/host**: api.starlink.com

TCP/IP settings

- **IP port**: 443
- **Bus address**: *ByPassProxy*. This must be filled in to bypass any possible proxy that could block the HTTP communication.

> [!NOTE]
> Using *ByPassProxy* may result in `Error : 12002. ERROR_WINHTTP_TIMEOUT` if the server requires routing through a security-enforcing proxy. In such cases, remove the *ByPassProxy* entry from *Bus address* to restore connectivity.

### Initialization

A newly created element will only start polling data if an active [Starlink Enterprise element](https://catalog.dataminer.services/details/d1dc1fae-0902-4cc3-9ae6-d1983d9596a3) with name **Starlink Enterprise** is available on the DMS and when both the **Client ID** and **Client Secret** are filled in on the **Configuration** page.

## How to Use

The connector uses JSON over HTTP to retrieve its data.

To see the actual traffic between the element and the device, a built-in DataMiner tool called Stream Viewer can be used. You can access it by right-clicking the element in the Surveyor and selecting **View** > **Stream Viewer**.

If you only see group 700 in the Stream Viewer, check the **Authentication** parameter and re-enter the client ID and client secret if the authentication failed.

A healthy element will show groups 700, 701, 702, 703, 704, 705 and 972 in the Stream Viewer.

Unexpected column names and user terminal alerts will be logged in the element log file. If you encounter these, please contact Skyline so that the connector can be corrected or extended. You can open the element log file by right-clicking the element in the Surveyor and selecting **View** > **Log**. However, note that lines in the element log file indicating *token_expired* can be safely ignored, as these are also added when nothing is wrong with the element.

When the **Info Logging Level** of the element log file is raised to *Level 1* or higher, you will see a line in the log file when no terminals are assigned to the account or when no services are active for the account.

### General Page

The General page contains the **Client ID**, the **Client Secret**, and the **Authentication** field. When the specified client ID and client secret have both been accepted by the API, the Authentication field will indicate *Successful*. The connector will update its access token every 15 minutes, just before it expires.

In case the traffic inside the Stream Viewer seems minimal, check if the Authentication parameter indicates *Successful*. If it instead indicates *Failed*, most likely the client ID or the client secret is not correct.

The polling mechanism is triggered after the value of the Client Secret parameter changes. This means that a Client Secret value change is required to trigger a new poll cycle after an incorrect Client ID is corrected.

> [!CAUTION]
> Changing the client secret will also remove all dynamic virtual elements if **Demo Mode** is **Enabled** on the Starlink Enterprise element.

The Configuration page also contains two telemetry request configuration parameters:

- **Telemetry Batch Size** represents the maximum number of telemetry entries to return in the response. The recommended batch size is ~65000 records per request (this is the maximum). If the batch does not have that size, it will return less. Keeping it at 65000 allows fast backpolling when needed.
- **Telemetry Linger Duration** represents the maximum number of milliseconds to collect telemetry entries. The recommended linger duration is ~15000 ms (this is the minimum) to ensure that all data points come in accurately. If the telemetry requests are timing out, please check the **Timeout of a single command (ms)** setting in the element configuration. Preferably, the timeout of a single command should be slightly bigger than the Telemetry Linger Duration.

With the **Poll Only Service Linked Terminals** toggle button you can enable a filter on the **User Terminals** query. This button is set to *Off* by default, which will poll all the user terminals from the management API whether they have a service line configured or not. Toggling the button to *On* will poll only user terminals that are linked to a service line.

> [!IMPORTANT]
> Enabling the **Poll Only Service Linked Terminals** filter will stop updating user terminals that do not have a service line configured. Those rows in the table will be removed after the specified cleanup time. If DVEs are enabled for terminals that do not have a service line configured, please disable them if you are using this filter.
