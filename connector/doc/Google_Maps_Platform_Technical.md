---
uid: Connector_help_Google_Maps_Platform_Technical
---

# Google Maps Platform

## About

The Google Maps Platform is a collection of location-based services provided by Google that allows organizations to integrate Google Maps functionalities into their system.
The Google Maps Platform connector interacts with the Google Maps Platform API to collect Environmental and Route data for smart-city applications.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination. Add one of the Google Maps Platform API endpoints. e.g. pollen.googleapis.com]
  - **IP port**: [The IP port of the destination. (default: *443*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]


### Initialization

The Google Maps Platform connector uses API key to communicate with the Google Maps Platform API. To generate API Key, the user needs to set up Google Cloud project before using this connector. Follow the steps in [this link](https://developers.google.com/maps/get-started?hl=en) to set up the Google Cloud project. Once the project is created and API Key generated, fill in the API Key on the General page of the connector.

### Redundancy

There is no redundancy defined.

## How to use

To get all the data in this connector, the user needs to define location(s) on the **Locations** table. In the context menu of this table (right-click), the user has to provide the name of the city and optionally the other fields. To get **Pollen** and **Air Quality** data, the Pollen and Air Quality fields need to be set to **Enabled**. The user can manually fill the latitude and longitude values for the given location or if left blank, the Geocoding API will be used to retrieve this information.

On the **Routes** page, the user has to fill in the **Origin** and **Destination** of the route using the Routes table context menu. The available locations are provided in the drop-down lists which are retrieved from the Locations table.

On the **Poll Manager** page, the user can control the polling state and frequency of each API per location/route. The user has to set a proper polling frequency since the API usage will depend on the polling frequency and number of locations defined on the Locations page.
The user can monitor the API usage on the API Usage page. The user can adjust the polling frequency of each API based on the Estimated API usage. The Request Count and Estimated Usage in this table takes into account the API calls and locations defined on this Dataminer element. If the API Key is used for other Dataminer elements or applications, those API Requests are not counted here.
