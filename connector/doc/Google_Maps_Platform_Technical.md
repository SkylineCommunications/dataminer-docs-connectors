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

To generate the API key, set up a Google Cloud project before you start using this connector. To do so, follow the steps under [Getting started with Google Maps Platform](https://developers.google.com/maps/get-started?hl=en).

Once the project has been created and the API key has been generated, go to the **General** page of the DataMiner element and fill in the API key.

## How to use

To get all the data in this connector, you will first need to define one or more locations in the **Locations** table. Right-click the table, select to add a location, and then provide the name of the city and optionally the other fields. To get **pollen** and **air quality** data, the Pollen and Air Quality fields need to be set to *Enabled*. You can manually fill in the latitude and longitude values for the given location, or leave it blank to have this information retrieved via the Geocoding API.

On the **Routes** page, fill in the **Origin** and **Destination** of the route via the right-click menu of the Routes table. The available locations are provided in the dropdown lists, which are retrieved from the Locations table.

On the **Poll Manager** page, you can control the polling state and frequency of each API per location/route. Make sure to set a proper polling frequency, as the API usage will depend on the polling frequency as well as on the number of locations defined on the Locations page.

On the **API Usage** page, you can monitor the API usage. Based on the estimated API usage on this page, you can adjust the polling frequency of each API on the Poll Manager page. The Request Count and Estimated Usage on the API Usage page take into account the API calls and locations defined in the DataMiner element. If the API key is also used for other DataMiner elements or applications, those API requests are not counted here.
