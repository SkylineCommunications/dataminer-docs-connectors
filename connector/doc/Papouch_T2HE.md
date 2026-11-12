---
uid: Connector_help_Papouch_T2HE
description: "Monitor a Papouch TH2E device over HTTP to view temperature, humidity, dew point, and recorded minimum and maximum measurements in DataMiner."
---

# Papouch T2HE

## About

Depending on the sensor connected to it, the Papouch **TH2E** is able to measure temperature and humidity, and calculate the dew point. The **Papouch T2HE** connector is an **HTTP** connector that is used to monitor this device.

> [!NOTE]
> The supported Papouch device is the **TH2E**. However, **T2HE** is the established name of the DataMiner connector in the Catalog.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy.*

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The element has the following data pages:

- **General**: Contains the measured values of temperature, humidity and dew point.
- **Extreme Values**: Displays the lowest and highest values that have been measured since the last reset or since the element was created. The information is displayed in a table with the values and the times those values were detected. The maximum and minimum limits defined by the user are also displayed.

## Notes

Supported firmware: 6.7/17 (created 26.02.2019)
