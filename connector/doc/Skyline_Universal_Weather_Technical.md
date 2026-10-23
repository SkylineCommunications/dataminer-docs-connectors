---
uid: Connector_help_Skyline_Universal_Weather_Technical
description: "Configure the Skyline Universal Weather connector, add locations, poll OpenWeather or Windy, and request weather from other elements via InterApp."
---

# Skyline Universal Weather

## About

The **Skyline Universal Weather** connector retrieves weather information from a weather API for a list of locations. Depending on the range, it supports the following service sources:

- **OpenWeather 2.5** and **OpenWeather 3.0** (One Call API): Current conditions, minutely, hourly, and daily forecasts, and national weather alerts. OpenWeather is available from version 1.0.0.4 onwards. OpenWeather 3.0 is available from version 1.0.2.3 onwards. In that version, the existing OpenWeather endpoint was renamed to OpenWeather 2.5.
- **OpenWeather Group**: Current conditions for several cities in one request. Available from range 1.0.1.x onwards.
- **Windy API** (Windy Point Forecast API v2): Forecasts per location, with a history table. Windy is available in range 1.0.4.x and from version 1.0.3.3 onwards.
- **Dark Sky**: Only available up to range 1.0.3.x. Dark Sky was removed in version 1.1.0.1.

Besides polling the configured locations, the connector can answer on-demand requests for a single coordinate, either from the ad hoc console or from other DataMiner elements.

> [!NOTE]
> Range 1.0.4.x is a separate line based on version 1.0.3.1. Its features are not necessarily available in ranges 1.0.3.x, 1.1.0.x, 1.1.1.x, and 1.2.0.x, and features added in those ranges are not necessarily available in range 1.0.4.x. Unless a section mentions a range, it applies to range 1.2.0.x.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The host of the API, e.g., `api.openweathermap.org`. In range 1.2.0.x, the connector builds the request URLs itself, based on the selected **Service Source** (`https://api.openweathermap.org:443` or `https://api.windy.com:443`), so any value can be entered.
- **IP port**: The IP port of the API. By default: *443*.

### Initialization

1. On the **Configuration** page, select the **Service Source**.
1. Open the page button of the selected source (e.g., **OpenWeather 2.5**, **OpenWeather 3.0**, or **Windy API**) and fill in the **API Key** and the **Max Number of Request (24 Hours)** that matches your API subscription.
1. For the Windy API, select the **Windy Forecast Model** and set **Windy API Polling Status** to *Enabled*.
1. If the DataMiner Agent needs a proxy to reach the internet, fill in the **Proxy Server** on the **Configuration** page. This setting is available from version 1.0.1.5 onwards.
1. On the **Locations** page, right-click the **Locations Overview** table and select **Add item**, or import a CSV file.

## How to Use

### General

The **General** page shows the **Service Status** (*OK*, *Connection Error*, *Integration Error*, *Max Number of Requests*, or *N/A*), the **Number of Requests (24 Hours)**, the **Number of Locations**, and the **Number of Ad-Hoc Locations**. The number of ad hoc locations also counts the requests received from other elements.

### Locations

Right-click the **Locations Overview** table to add, edit, or delete locations. A location needs a **Name**, a **Latitude**, and a **Longitude**. From version 1.1.0.3 onwards, latitudes must be between -90 and 90, and longitudes between -180 and 180. Masked locations are not polled.

From version 1.0.1.6 onwards, you can import locations from a CSV file with the columns **Name**, **Description**, **Latitude**, and **Longitude**, in this order. Use a period as the decimal separator for the coordinates.

### Weather Forecast and Forecast Tables

The **Weather Forecast** page shows a tree per location with the current conditions, the minutely, hourly, and daily forecasts, and the national weather alerts. The **Forecast Tables** page shows the same data as tables. The locations are polled every **Auto Processing Time** (default: 3600 seconds).

The **Unit System** (*Imperial* or *Metric*) and **Ratio Unit** (*Relative* or *Percentage*) on the **Configuration** page define how values are displayed.

In range 1.0.4.x and from version 1.1.1.1 onwards, the display key format of the tables can be changed with the display key format parameters. Version 1.1.1.1 changes the display keys, so existing alarms are updated with the new display keys.

### Windy API Forecast Tables (Range 1.0.4.x and from Version 1.0.3.3 Onwards)

When the **Service Source** is *Windy API* and **Windy API Polling Status** is *Enabled*, the connector polls each location with the selected **Windy Forecast Model**.

- **Windy Forecast Last Polled**: The time of the last Windy API request.
- **Windy Forecast Table**: The forecasts returned by the API, in fixed 3-hour intervals for at least the next 7 to 10 days. All forecast values are surface-level values.
- **Windy Forecast History Table**: When a forecast expires, it is moved to this table. In range 1.2.0.x, forecasts that belong to another forecast model or to a deleted location are also moved to this table. You can delete history entries with the context menu of the table.

### Windy API Settings

The **Windy API** page button on the **Configuration** page contains the following settings:

- **Windy API Key**: The Point Forecast API key.
- **Windy Max Number of Request (24 Hours)**: The maximum number of Windy API calls per day. Configure this based on your Windy account to avoid unnecessary charges.
- **Windy Forecast Model**: The forecast model to use:
  - *arome*: France and surrounding areas.
  - *iconEu*: Europe and surrounding areas.
  - *gfs*: Global model.
  - *namConus*: The USA and surrounding areas (Canada, Mexico).
  - *namHawaii*: Hawaii.
  - *namAlaska*: Alaska and surrounding areas.
- **Windy API Polling Status** (from range 1.0.3.x onwards): Enables or disables the polling of the Windy API.

In range 1.0.4.x, the page also contains the following parameters:

- **Number of Windy API Requests Made (24 Hours)**: The number of Windy API requests made by the connector. This value is reset every 24 hours.
- **Windy API Polling Frequency**: The frequency at which the connector makes Windy API requests.

In all ranges with Windy support, the connector sends the Windy requests to the `api/point-forecast/v2` endpoint. For more information about the Windy API, see the [Windy Point Forecast API documentation](https://api.windy.com/point-forecast/docs).

### Ad-Hoc Forecast

Use the ad hoc console to request the current conditions of one coordinate without adding a location:

1. Make sure **Console Status** is *Enabled* on the **Ad-Hoc** page (page button on the **Configuration** page).
1. On the **Ad-Hoc Forecast** page, select *Current Conditions* as **Request Type**.
1. In **Request Parameters**, enter the coordinate as `latitude,longitude`, e.g., `51.05,3.72`.
1. Enter a **Location Name** and optionally a **Location Description**.
1. Click **Apply**.

The result is added to the **Ad-Hoc Current Conditions** table. **Clear All** removes all entries.

When **Auto Delete** is *Enabled* (default), entries older than the **Auto Delete Delay** are removed automatically. With the default delay, *Real-Time*, all entries are removed at the next cleanup. In range 1.2.0.x, the cleanup runs every 30 seconds. In ranges 1.0.0.x to 1.0.2.x, it runs every hour.

### Requests from Other Elements

Other elements can request the current weather of a coordinate when **Inter Element Service** is *Enabled* (default) on the **Ad-Hoc** page. The mechanism depends on the range:

- **Prior to range 1.0.2.x**, the requesting element sets a JSON request with the **Request Type**, **Request Parameters**, **Location Name**, and **Location Description** on the listener parameter (PID 283). The connector then sends the response back to the response listener parameter of the requesting element.
- **From range 1.0.2.x onwards**, the listener parameter is no longer used. Other elements communicate with the connector through the InterApp framework, as described below.

In both cases, the connector requests the weather from the API, adds the result to the **Ad-Hoc Current Conditions** table, and sends the response to the requesting element.

### InterApp Support (From Range 1.0.2.x Onwards)

Other elements can request the current weather of a coordinate through the InterApp framework. The connector receives the messages on parameter 9000000. The result is also added to the **Ad-Hoc Current Conditions** table.

The behavior differs per version:

- From version 1.2.0.1 onwards, the connector replies with `Reply` when the requester expects a reply (InterApp 1.1.x broker), and otherwise sends the response to the return address of the request. Range 1.2.0.x requires DataMiner 10.4.0.0-14003 or higher.
- From version 1.2.0.2 onwards, every request receives exactly one response. Requests that cannot be handled receive a response with **Status** *Error* instead of no response, and each Skyline Universal Weather element has its own request buffer. In older versions, a request that cannot be handled can remain unanswered, so the requester only detects this through its own timeout.

InterApp requests are only answered with weather data when the **Service Source** is *OpenWeather 2.5* or *OpenWeather 3.0*. From version 1.2.0.2 onwards, with *Windy API*, every request receives a failed response.

The messages are based on the `Skyline.DataMiner.Core.InterAppCalls.Common` NuGet package. No separate ConnectorAPI package is available, so the sender must define the message classes with the same names, namespace (`WeatherApi`), and properties as the connector. Pass the following known types, in this order:

1. `WeatherRequest`
1. `WeatherResponse`

#### Request

A **WeatherRequest** contains the following properties:

- **RequestType**: Must be *Current Conditions*.
- **Query**: The coordinate as `latitude,longitude` in signed decimal degrees, with a period as the decimal separator, e.g., `51.05,3.72`.
- **Name**: The name of the location. Required.
- **Description**: An optional description of the location.

#### Response

A **WeatherResponse** contains the following properties:

- **Guid**: The **Guid** of the request.
- **Status**: *OK* if weather data is returned, *Error* if the request could not be handled. An *Error* response contains no weather data.
- **Provider**: The weather provider, e.g., *OpenWeather*.
- **Summary**: A short description of the current weather.
- **PrecipitationType**: The type of precipitation.
- **PrecipitationProbability**: Not provided for OpenWeather. The value is *-1*.
- **Time**: The time of the current conditions.

From version 1.2.0.2 onwards, a request receives a response with **Status** *Error* in the following cases:

- The request type, a valid coordinate, or the name is missing.
- No API key is configured for the selected service source, or the service source does not support InterApp requests.
- The **Max Number of Request (24 Hours)** is reached.
- The API returns an error or an invalid response.
- No API response is received within 60 seconds.
- The request waits in the buffer longer than the **Clear Buffer Timer** (default: 300 seconds).
- The buffer is cleared with the **Clear All Buffer** button.
- **Inter Element Service** is set to *Disabled* on the **Ad-Hoc** page.

#### Example

The following QAction snippet requests the weather for a coordinate and reads the response:

```csharp
var request = new WeatherRequest
{
    Name = "Site A",
    Description = "Site A",
    RequestType = "Current Conditions",
    Query = latitude.ToString(CultureInfo.InvariantCulture) + "," + longitude.ToString(CultureInfo.InvariantCulture),
};

var knownTypes = new List<Type> { typeof(WeatherRequest), typeof(WeatherResponse) };

IInterAppCall call = InterAppCallFactory.CreateNew();
call.Messages.Add(request);
call.Source = new Source("Weather request", protocol.DataMinerID, protocol.ElementID);
call.ReturnAddress = new ReturnAddress(agentId, elementId, 9000001);

var response = call
    .Send(protocol.SLNet.RawConnection, agentId, elementId, 9000000, TimeSpan.FromSeconds(120), knownTypes)
    .OfType<WeatherResponse>()
    .FirstOrDefault();

if (response == null || response.Status == ResponseStatus.Error)
{
    // No weather data available.
}
```

The connector handles the requests one at a time, in the order in which they are received. Use a timeout that allows for the requests already in the buffer.

#### Buffer Monitoring

The **Debug** page shows the InterApp buffer when **Debug** is enabled on the **Configuration** page:

- **Buffer Size**: The number of requests that are waiting or being handled.
- **Buffer Content**: The waiting requests. From version 1.2.0.2 onwards, the request being handled is listed first.
- **Last Received Interelement**: The time when the last request was received.
- **Clear Buffer Timer** (from version 1.0.3.4 onwards): The maximum time a request can wait in the buffer. Set it to *Disabled* to keep requests until they are handled.
- **Clear All Buffer** (from version 1.0.3.4 onwards): Clears the buffer. From version 1.2.0.2 onwards, all requests in the buffer receive a failed response first.

Prior to version 1.2.0.2, **Last Received Interelement** is only updated while **Debug** is enabled. From version 1.2.0.2 onwards, all buffer parameters are always updated.

### Troubleshooting

- **The Service Status is Max Number of Requests**: The **Number of Requests (24 Hours)** reached the configured maximum. Increase the maximum within the limits of your API subscription, mask locations, or increase the **Auto Processing Time**.
- **The Service Status is Connection Error**: Check the API key, the **Proxy Server**, and whether the DataMiner Agent can reach `api.openweathermap.org` or `api.windy.com`.
- **An InterApp request always returns Status Error** (from version 1.2.0.2 onwards): Check the element log. Each failed request is logged with its reason, e.g., *Request URL or API key not available*. Also check that the **Service Source** is *OpenWeather 2.5* or *OpenWeather 3.0*, that **Inter Element Service** is *Enabled*, and that the **Query** uses a period as the decimal separator.
- **An InterApp request times out**: Check that the request is sent to the correct element, that the element is active, and that the timeout is long enough for the requests in the buffer. Prior to version 1.2.0.2, requests that cannot be handled are not answered, so check the same settings as for a response with **Status** *Error*. If the timeouts occur in range 1.2.0.x while **Debug** is disabled, upgrade to version 1.2.0.2 or higher.
- **The Windy tables stay empty**: Check that the **Service Source** is *Windy API*, that **Windy API Polling Status** is *Enabled*, and that a **Windy API Key** is filled in.

## Notes

- Dark Sky is only supported up to range 1.0.3.x. It was removed in version 1.1.0.1.
- **Listener PID** (prior to range 1.0.2.x): 283. From range 1.0.2.x onwards, the listener parameter is no longer used, because the element communication uses InterApp calls instead.
- The Windy API URL is built in and uses the same **Proxy Server** as the OpenWeather APIs.
- For more information about the APIs, see the [OpenWeather One Call API 3.0](https://openweathermap.org/api/one-call-3) and the [Windy Point Forecast API](https://api.windy.com/point-forecast/docs) documentation.
