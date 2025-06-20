---
uid: Connector_help_Starlink_Enterprise
---

# Starlink Enterprise

## About

The purpose of this connector is to monitor Starlink devices through the Telemetry API and the Management API over HTTP using JSON files.

Starlink is an internet service that uses a satellite constellation in a low Earth orbit to deliver high-speed low-latency broadband internet. Because Starlink satellites are in a low orbit, at about 550 km from Earth, the round-trip data time between the user and a satellite is significantly lower compared to internet services that make use of single geostationary satellites.

The Starlink Telemetry API is a low-latency API for accessing the telemetry data from Starlink devices. This API is only available for enterprise accounts with an account manager. It is designed for users that have their own data infrastructure to monitor Starlink devices remotely. The API is stateless and will only respond with current telemetry data.

The Starlink Management API is used to activate, deactivate, and otherwise manage Starlink user terminals. Next to this, it can return paginated results containing data usage for the current and previous billing cycles for service lines on an account. Similar to the Telemetry API, this API is only available for enterprise accounts with an account manager.

The Starlink Enterprise connector was previously known as the Starlink Telemetry API connector. The name was changed to Starlink Enterprise when calls towards the Management API were added. The Starlink Enterprise 1.0.0.1 is the same connector as the Starlink Telemetry API 1.0.0.4. If you have any elements that are still using the Starlink Telemetry API, we recommend upgrading these to the latest version of the Starlink Enterprise connector.

> [!NOTE]
> **LEGAL NOTE**: This connector (or package) is intended solely for use in production with Skyline's usage-based services model. Any other use is prohibited. For more detailed information, see [Usage-based services](https://aka.dataminer.services/usage-based-services-docs). For inquiries regarding commercial production usage, contact Skyline Sales at <sales@skyline.be>.

> [!TIP]
> To optimize your use of this connector, we recommend deploying our **Standard Product Solution** [Starlink Enterprise](https://catalog.dataminer.services/details/66a4c259-0fb1-4c27-aede-8bbd3a4925d0) via the Catalog. This way, you will also be able to use the complementary low-code app and standard available dashboards.

## Key Features

- **Conditional Telemetry Polling**: Allows for telemetry polling per account. Telemetry is being polled every minute, content is stored using history sets for accurate backpolling.

- **User Terminal Details**: Details on user terminals and service lines. The User Terminal Device Name is the service nickname if a service is active on the user terminal. The Device ID is used as Device Name if no service is active.

- **Data Usage**: Review and monitor your data usage per month or day by type of data consumed (Fixed or Mobile, Priority or Standard). Additional services or data consumed beyond the limit is shown in the Overage Lines table. There is a 12 month retention to the Monthly Data Usage table.

- **Simulation Mode**: An extension that utilizes built-in logic based on mock accounts and user terminals to replicate real-world scenarios. The simulation is enabled during the element creation and will run until you enter the Client ID and Client Secret**. After that, the simulation stops and the element starts polling real data if the credentials are valid. History simulation data was added for the demo terminal "Skyline demo cruise_UT*74d101" to allow location tracking.

- **User Terminal Dynamic Virtual Elements**: The [Starlink Enterprise - User Terminal](xref:Connector_help_Starlink_Enterprise_-_User_Terminal) connector is exported to be able to create a separate child element (DVE) for each known user terminal. These DVEs contain only data related to the user terminal.

- **Ticketing System Integration**: It's possible to export a CSV file for customer data elements to ingest for ticketing. This CSV file contains basic info about all terminals with valid service lines.

- **Multithreading**: A dedicated thread is used for management/config polling next to the main protocol execution thread to increase polling efficiency.

## Use Cases

### Use Cases 1

**Challenge**: Mark offline terminals.

**Solution**: The connector compares the telemetry data with the management data to distinguish the offline terminals.

**Benefit**: Makes it clear which terminals can be ignored.

### Use Cases 2

**Challenge**: Show data usage as stacked bar graph.

**Solution**: Data usage tables are built to easily create a stacked bar graph in a dashboard or low code app.

**Benefit**: Shows the data usage similar to the web interface.

### Use Cases 3

**Challenge**: Create services with parameters from a subset of terminals.

**Solution**: Ability to create a Dynamic Virtual Element per user terminal.

**Benefit**: Monitor the KPIs of the most relevant terminals only.

### Use Cases 4

**Challenge**: Too much requests send from the same IP address.

**Solution**: Conditional polling of telemetry data through Polling togglebutton column.

**Benefit**: Multiple elements can be created on different hosts. Accounts A and B can be polled from server Y and accounts C and D can be polled from server Z. The overarching dashboard or low code app can combine this data to show the info of every account.

### Use Cases 5

**Challenge**: New column names and changing alert names.

**Solution**: Unexpected telemetry column names and alerts will be logged in the element log file.

**Benefit**: Element will indicate by itself when the connector needs to be extended.

### Use Cases 6

**Challenge**: Monitoring based on alerts.

**Solution**: Each row in the Alerts table represents an alert that comes from a user terminal or from a router. Alerts will persist for as long as they are active.

**Benefit**: Web interface alerts are visible in the DataMiner alarm console.

## Technical Reference

### Prerequisites

- **DataMiner Feature Release 10.4.2.0 – 13915** is needed for being able to install this connector.

- **Starlink API access**: API credentials (Client ID, Client Secret) are required for authentication to enable polling.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Starlink_Enterprise_Technical).
