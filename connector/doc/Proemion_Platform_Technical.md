---
uid: Connector_help_MyUplink_Platform_Technical
---
# MyUplink Platform

## About

The **Proemion Platform** connector integrates the Proemion cloud-based telematics platform into DataMiner, enabling centralized monitoring, data aggregation, and operational insight for connected industrial machines. The connector provides a scalable and structured view of large fleets of geothermal drilling machines and associated communication units.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]

### Initialization

The Proemion Platform uses OAuth 2.0 (Client Credentials) for authentication. For the connector to start polling data from the data source, you will need to provide the **Client ID**, and **CLient Secret** on the **Element Settings** page.

Once you fill in valid Client ID and Client Secret, click the **Connect** button for the connector to authomatically generate the access token used for the polling of data from the API.

## How to Use

You can configure the polling of the parameters on the **Communications Settings** sub-page under **Element Settings** page. When adjusting the polling intervals, keep in mind that the API is rate limited.

You can enable/disable the polling of each machine in the Machines table using the Polling column. This gives flexibility on which machines to actively monitor and also to comply with the rate limit by disabling the polling of machines which are not going to be actively monitored.
