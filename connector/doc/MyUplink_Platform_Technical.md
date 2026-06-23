---
uid: Connector_help_MyUplink_Platform_Technical
---
# MyUplink Platform

## About

The **MyUplink Platform** connector integrates the MyUplink cloud platform into DataMiner, enabling monitoring, control, and data aggregation of connected HVAC and energy systems (e.g., heat pumps, indoor climate systems). The connector communicates with the MyUplink REST API, retrieves device and parameter data, and maps this information into DataMiner elements and parameters.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

### Initialization

The myUplink PRO API uses OAuth 2.0 (Client Credentials and Authorization Grant Code flow) for authentication. For the connector to start polling data from the data source, you will need to provide the **Client ID**, **Client Secret**, and **Authorization Code** on the **Element Settings** page.

The **Authorization Code** is generated as follows:

1. Go to the API's login page by starting in the user interface of the application consuming the integration, which will redirect you to the login page `api-pro.myuplink.com/oauth/login`. This endpoint is part of the *Identity* section of the API.

   Alternatively, you can use the URL `https://api-pro.myuplink.com/oauth/authorize?response_type=code&client_id={clientId}&scope=READSYSTEM%20WRITESYSTEM%20offline_access&redirect_uri={redirectUri}&state=x`, replacing `{clientId}` with your **Client ID** and `{redirectUri}` with a valid URL that matches the field **Callback URL** during client registration.

1. Log in using your username and password.

1. Select the service partner you want to log in with.

1. Grant permission to associate your account with the client and permissions.

   You will be redirected to the UI of the application consuming the integration.

1. Copy the generated code as shown in the example below:

   ![Example of the URL containing the generated code](~/connector/images/599379631-c57f58a1-745c-4d1e-9389-787f45d15e6b.png)

1. On the **Element Settings** page of the element, fill in the copied code in the **Authorization Code** parameter.

When you have filled in a valid Client ID, Client Secret, and Authorization Code, click the **Connect** button for the connector to automatically generate the access token used for the polling of data from the API.

## How to Use

You can configure the polling of the parameters on the **Communications Settings** subpage of the **Element Settings** page. When adjusting the polling intervals, keep in mind that the API is rate-limited.

You can enable or disable the polling of each device in the **Devices** table using the **Polling** column. This allows you to determine which devices to actively monitor and makes it easier to comply with the rate limit by disabling the polling of devices that require no active monitoring.

If you change the **numeric value** of a parameter on the **Parameters** page, make sure the provided values are within the allowed range of the parameters and use the correct step size.
