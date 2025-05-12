---
uid: Connector_help_Google_Maps_Platform_Technical
---

# Google Maps Platform

## About

The Google Maps Platform is a collection of location-based services provided by Google that allows organizations to integrate Google Maps functionalities into their system.

This Google Maps Platform connector interacts with the Google Maps Platform API to collect environmental and route data for smart-city applications.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The Google Maps Platform API endpoint, e.g. *pollen.googleapis.com*.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

The Google Maps Platform connector uses an API key to communicate with the Google Maps Platform API.

To generate the API key, set up a Google Cloud project before you start using this connector. To do so, follow the steps under [Getting started with Google Maps Platform](https://developers.google.com/maps/get-started).

Once the project has been created and the API key has been generated, go to the **General** page of the DataMiner element and fill in the API key.

## How to use

The Google Maps Platform connector offers monitoring capabilities for various city and metrics. To utilize these features, you need to set up a Google Cloud project and obtain a valid API key. To access all the data provided by this connector, you must first define one or more locations in the Locations table.

You can view the full list of available APIs offered by the Google Maps Platform [here](https://mapsplatform.google.com/maps-products/).

Below is detailed information about the various data pages available in the element.

### General

On this page, specify the API Key that will be used to interact with the Google Maps Platform during element initialization. To ensure full functionality of the connector, this API Key should have the following APIs enabled: *Routes*, *Air Quality*, *Pollen*, and *Geocoding*.

### Locations
On this page, specify the locations you wish to monitor. Use the table's context menu (right-click on the table) and select *Add Location...*. In the context menu, provide the name of the city and optionally fill in the other fields.

To retrieve air quality and pollen data, ensure the *Pollen* and *Air Quality* fields are set to *Enabled*. You can manually enter the latitude and longitude values for the location, or leave these fields blank to have the information retrieved via the Geocoding API.

### Air Quality
On this page, you can monitor the Air Quality Index (AQI) for each designated location. The AQI category (e.g., good, moderate, unhealthy) and the main pollutant are also clearly identified.

### Pollutants
This page provides a comprehensive list of pollutants for each designated location, along with their concentration values and main health effects.

### Health Recommendations
This page allows you to select a location and view the latest health recommendations for different population groups (e.g., children, elderly, general population).

### Pollen
The Pollen page provides detailed information about the Universal Pollen Index (UPI) for each designated location and pollen type. It includes the UPI categorization (e.g., low, moderate, high) and relevant health recommendations.

### Plant Info
On this page, you will find a comprehensive list of UPIs for each plant at the designated locations. The UPI categorization, the season in which each pollen type is most common, and any cross-reactions are also presented.

### Routes
On the Routes page, fill in the *Origin* and *Destination* of the route using the Routes table's context menu (right-click on the table). The available locations are provided in the dropdown lists, which are populated from the Locations table.

### Poll Manager

On the Poll Manager page, you can control the polling state and frequency for each API per location and route. Set an appropriate polling frequency, as API usage will depend on both the polling frequency and the number of locations defined on the Locations page.

### API Usage

On the API Usage page, you can monitor API usage. Based on the estimated API usage shown on this page, you can adjust the polling frequency for each API on the *Poll Manager* page. The Request Count and Estimated Usage on the API Usage page reflect the API calls and locations defined in the DataMiner element. **If the API key is also used for other DataMiner elements or applications, those API requests are not counted here**.

> [!IMPORTANT]
> The estimated number of API requests is an approximation for the current month based on the current configuration of the location and poll manager. Please note that the API Key used by this element might also be utilized by other elements or third-party applications. If this is the case, such requests are not included in this estimation.
>
> The free limit indication is provided by Google Maps Platform. Be aware that Google may have changed policies since the connector development. Please verify that the presented values are still up-to-date with Google's policies, and inform us if you find that they need to be updated. You can review Google's API request policies [here](https://mapsplatform.google.com/lp/maps-apis/).