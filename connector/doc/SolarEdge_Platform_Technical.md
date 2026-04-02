---
uid: Connector_help_SolarEdge_Platform_Technical
---

# SolarEdge Platform

## About

The SolarEdge Platform connector enables centralized monitoring of SolarEdge systems by integrating with the SolarEdge API. It provides users with access to real-time solar site data and inverter data for linked locations directly within DataMiner.

## Configuration

### Connections

#### HTTP Connection - IP Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The URL of the SolarEdge API.
- **IP port**: The port used to connect to the SolarEdge API.

### Initialization

SolarEdge is an open API, so the connector will begin fetching data from the moment an account key is provided on the **Element Settings** page.

> [!IMPORTANT]
> The free tier of the SolarEdge API allows up to **300 requests per day**. Be mindful of your polling configuration: excessive requests or retrieving too many variables at short intervals may exceed this limit, resulting in throttling or temporary access restrictions. Adjust polling frequency and selected variables carefully to stay within the allowed usage.

## How to Use

Once an element is configured, the connector automatically starts polling data from the SolarEdge API, retrieving current linked sites, real-time inverter data, and real-time meter data for all linked sites.

On the **API Configuration** page, you can adjust polling parameters and select which weather variables to retrieve from the API.
