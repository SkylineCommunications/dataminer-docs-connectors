---
uid: Connector_help_Skyline_Universal_Weather
---

# Skyline Universal Weather

## About

The **Skyline Universal Weather** connector is designed to retrieve weather conditions from a weather **API** source of the user's choice for selected locations specified by the user.

This connector uses an HTTPS connection to communicate with the selected API. The weather information is then retrieved for the locations specified by the user.

![Skyline Universal Weather](~/connector/images/SkylineUniversalWeather_Overview.png)

## Key Features

- **Compatability with different Weather API's**: The connector is highly versatile, supporting multiple API services to provide flexibility based on your preferences and requirements.
Currently, it is compatible with three distinct weather APIs: OpenWeather OneCall 2.5, OpenWeather OneCall 3.0, and Windy Point-Forecast API v4

- **Access to a wide range of meteorological data**:  Access to specialized information such as wind patterns or precipitation trends.

- **Access to historical data and forecasts**: Access to tables with daily, hourly, and minutely forecast reports. 

- **Get weather conditions on an ad-hoc basis**: The connector allows you to be able to query the API on an ad-hoc basis.

## Use Cases

Certain environmental factors, such as heavy rainfall, strong winds, or extreme temperatures, can impact system performance, depending on what is being monitored, often leading to interference, power outages, or service disruptions. By integrating real-time or historical weather data into these reports, issues can more effectively diagnosed. This added layer of context enhances accuracy and ensures that external weather-related factors are properly accounted for, streamlining troubleshooting efforts and improving overall response times.

- On the Configuration page, you can define the API Service Source, set essential parameters like proxy settings and request limits, and choose units for forecast data.

- On the Locations page, you have the flexibility to manually input the specific locations you wish to monitor for weather data. 

- The connector can retrieve current weather data from OpenWeather either manually via the Ad-Hoc Console or automatically through the InterApp framework, which enables external elements to trigger requests as needed. This reduces unnecessary API calls, helps manage usage quotas efficiently, and supports ticketing and diagnostics through response messages.

## Technical info

> [!NOTE]
> For detailed technical information, refer to the [Technical help page](xref:Connector_help_Skyline_Universal_Weather_Technical).
