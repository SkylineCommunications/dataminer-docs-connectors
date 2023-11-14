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

- **IP port:** 443
- **Bus address**: *ByPassProxy*. This must be filled in to bypass any possible proxy that could block the HTTP communication.

### Initialization

A newly created element will only start polling data when both the **Client ID** and **Client Secret** are filled in on the **Login** page.

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

> [!NOTE]
> Keep in mind that the tables User Terminals, Alerts, and Routers can be empty even if polling is enabled for at least one account, the Authentication parameter indicates *Successful*, and groups 700-702 are shown in the Stream Viewer.

### General Page

The General page contains the **User Terminals** table. This table shows the Starlink terminals that are linked to the accounts for which polling is enabled.

### Alerts Page

Each row in the **Alerts** table represents an alert that comes from a user terminal. Alerts will persist for as long as they are active.

### Routers Page

Information related to routers is stored in the **Routers** table.

### Login Page

The Login page contains the **Client ID**, the **Client Secret** and the **Authentication** field. When both Client ID and Client Secret are accepted by the API, the Authentication field will indicate *Successful*, and data will start appearing in the element.

In case **no data** appears in the element and traffic inside the Stream Viewer seems minimal, check if the Authentication parameter indicates *Successful*. If it instead indicates *Failed*, this means that the Client ID or the Client Secret is not correct.

The polling mechanism is triggered after a Client Secret value change. This means that a Client Secret value change is required to trigger a new poll cycle after an incorrect Client ID is corrected.

### Accounts Page

All known accounts are listed in the Accounts table. Each row in this table contains a polling toggle button. No telemetry will be polled by default. The toggle button of every row will indicate *Disabled* after element creation. You will need to enable polling for the relevant accounts to be able to see data in the following tables: User Terminals, Alerts, and Routers.

> [!NOTE]
> Keep in mind that after you enable polling for one or more accounts, it can take some time before data is visible in the tables User Terminals, Alerts, and Routers. There is no trigger after changing one or more toggle buttons. Every timer cycle, the connector checks for which accounts polling is enabled.
