---
uid: Connector_help_MyUplink_Platform_Technical
---
# MyUplink Platform

## About

The **MyUplink Platform** Connector integrates the MyUplink cloud platform into DataMiner, enabling monitoring, control, and data aggregation of connected HVAC and energy systems (e.g., heat pumps, indoor climate systems).
The connector communicates with the MyUplink REST API, retrieves device and parameter data, and maps this information into DataMiner elements and parameters.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination.]

### Initialization

The myUplink PRO API uses OAuth 2.0 (Client Credentials and Authorization Grant Code flow) for authentication. For the connector to start polling data from the data source, you will need to provide the **Client ID**, **CLient Secret** and **Authorization Code** on the **Element Settings** page.
The **Authorization Code** is generated as follows:
- The user usually starts in the user interface (UI) of the application consuming the integration.
- The application redirects the user to the APIs login page api-pro.myuplink.com/oauth/login. This endpoint is part of the Identity section of the API.
- To go to the APIs login page, the user can also use the following URL: https://api-pro.myuplink.com/oauth/authorize?response_type=code&client_id={clientId}&scope=READSYSTEM%20WRITESYSTEM%20offline_access&redirect_uri={redirectUri}&state=x
  where **{clientId}** must be replaced with your **Client ID** and **{redirectUri}** must be replaced by a valid URL which should match the field **Callback URL** during client registration
- The user logins with his user and password details.
- The user selects the service partner they want to login with.
- The user grants permission to associate his account to the client and permissions.
- The user is redirected back to the UI of the application consuming the integration.
    <img width="1467" height="64" alt="image" src="https://github.com/user-attachments/assets/c57f58a1-745c-4d1e-9389-787f45d15e6b" />
- Then copy the generated code as shown in the picutre above and fill in the **Authorization Code** parameter with this value on the Element Settings page.

Once you fill in valid Client ID, Client Secret and Authorization Code, click the Connect button for the connector to authomatically generate the access token used for the polling of data from the API.

## How to Use

You can configure the polling of the parameters on the **Communications Settings** sub-page under **Element Settings** page. When adjusting the polling intervals, keep in mind that the API is rate limited.

You can enable/disable the polling of each device in the Devices table using the Polling column. This gives flexibility on which devices to actively monitor and also to comply with the rate limit by disabling the polling of devices which are not going to be actively monitored.

When changing the **Numeric Value** of a parameter on the **Parameters** page, make sure the provided values are within the allowed range of the paraemters with the correct step size.
