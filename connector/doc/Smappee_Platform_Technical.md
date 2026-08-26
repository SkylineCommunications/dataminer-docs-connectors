---
uid: Connector_help_Smappee_Platform_Technical
---

# Smappee Platform

## About

TThe Smappee Platform connector enables centralized monitoring of Smappee devices by integrating with the Smappee API. It provides users with access to real-time charging data directly within DataMiner.

## Configuration

### Connections

#### HTTP Connection - IP Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The URL of the Smappee API.
- **IP port**: The port used to connect to the Smappee API.

### Initialization

Smappee is an open API, so the connector will begin fetching data from the moment the **Client ID**, **Client Secret**, **Username**, and **Password** are provided on the **Element Settings** page.

## How to Use

Once an element is configured, the connector automatically starts polling data from the Smappee API, retrieving current linked sites, real-time inverter data, and real-time meter data for all linked sites.

On the **Communication Settings** page, you can adjust polling parameters and select which weather variables to retrieve from the API.
