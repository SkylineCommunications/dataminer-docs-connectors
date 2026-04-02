---
uid: Connector_help_Starlink_Enterprise_Account
---

# Starlink Enterprise Account

## About

The purpose of this connector is to monitor Starlink devices through the Telemetry API and the Management API over HTTP using JSON files.

Starlink is an internet service that uses a satellite constellation in a low Earth orbit to deliver high-speed low-latency broadband internet. Because Starlink satellites are in a low orbit, at about 550 km from Earth, the round-trip data time between the user and a satellite is significantly lower compared to internet services that make use of single geostationary satellites.

The Starlink Telemetry API is a low-latency API for accessing the telemetry data from Starlink devices. This API is only available for enterprise accounts with an account manager. It is designed for users that have their own data infrastructure to monitor Starlink devices remotely. The API is stateless and will only respond with current telemetry data.

The Starlink Management API is used to activate, deactivate, and otherwise manage Starlink user terminals. Next to this, it can return paginated results containing data usage for the current and previous billing cycles for service lines on an account. Similar to the Telemetry API, this API is only available for enterprise accounts with an account manager.

Elements that are created based on this connector do not show anything. This connector is designed for querying the Starlink API V2 only. A [Starlink Enterprise element](https://catalog.dataminer.services/details/d1dc1fae-0902-4cc3-9ae6-d1983d9596a3) is required on the DMS to make the polled information visible, and available for alarm monitoring and trending.

Since the introduction of the Starlink API V2, credentials are needed per account. These credentials have to be entered in the Starlink Enterprise Account element. The name of the Starlink Enterprise Account element has to match the **account name**.

> [!NOTE]
> **LEGAL NOTE**: This connector (or package) is intended solely for use in production with Skyline's usage-based services model. Any other use is prohibited. For more detailed information, see [Usage-based services](https://aka.dataminer.services/usage-based-services-docs). For inquiries regarding commercial production usage, contact Skyline Sales at <sales@skyline.be>.

> [!TIP]
> To optimize your use of this connector, we recommend deploying our **Standard Product Solution** [Starlink Enterprise](https://catalog.dataminer.services/details/66a4c259-0fb1-4c27-aede-8bbd3a4925d0) via the Catalog. This way, you will also be able to use the complementary low-code app and standard available dashboards.

## Key Features

- **Conditional polling**: Configure telemetry and management information polling per account.

- **User terminal filtering**: Only poll user terminals that are linked to a service line.

## Use Cases

### Load Balancing

**Challenge**: Ignoring non-serving user terminals.

**Solution**: The connector allows the polling of the user terminals that are linked to a service line only.

**Benefit**: Smaller content of the User Terminals table, available in the Starlink Enterprise element.

## Technical Reference

### Prerequisites

- **DataMiner Main Release 10.4.0** or higher.

- **Starlink API access**: API V2 credentials per account (Client ID, Client Secret) are required for authentication.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Starlink_Enterprise_Account_Technical).
