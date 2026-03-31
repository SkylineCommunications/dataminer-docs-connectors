---
uid: Connector_help_OpenMeteo_Weather_Technical
---

# Open-Meteo Weather

## About

The Open-Meteo Weather connector collects real-time weather data and forecasts from the Open-Meteo API, enabling users to monitor conditions for all configured locations directly in DataMiner.

## Configuration

### Connections

#### HTTP Connection - IP Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The URL of the Open-Meteo Weather API.
- **IP port**: The port used to connect to the Open-Meteo Weather API.

### Initialization

Open-Meteo is a free and open API, so the connector will begin fetching weather data without any additional credentials. However, users with a commercial license can provide an API key in the **Element Settings**.

> [!IMPORTANT]
> The free tier of the Open-Meteo API allows up to **300,000 requests per month**. Be mindful of your polling configuration: excessive requests or retrieving too many variables at short intervals may exceed this limit, resulting in throttling or temporary access restrictions. Adjust polling frequency and selected variables carefully to stay within the allowed usage.

## How to Use

Once an element is configured, the connector automatically starts polling data from the Open-Meteo API, retrieving current weather conditions, quarter-hourly forecasts, and hourly forecasts for all configured locations.

- The **Locations** page allows you to add new locations by specifying the coordinates for each site. The connector polls weather data individually for every configured location.
- On the **API Configuration** page, you can adjust polling parameters and select which weather variables to retrieve from the API.
