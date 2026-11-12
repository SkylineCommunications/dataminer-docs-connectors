---
uid: Connector_help_Papouch_T2HE
description: Learn how to configure and use the Papouch T2HE HTTP connector to monitor the Papouch TH2E Ethernet thermometer and hygrometer.
---

# Papouch T2HE

The **Papouch T2HE** connector uses **HTTP** to monitor the [Papouch TH2E Ethernet thermometer and hygrometer](https://en.papouch.com/th2e-ethernet-thermometer-and-hygrometer-p4825/?vid=2374). Depending on the connected sensor, the device can measure temperature and humidity, and calculate the dew point.

> [!NOTE]
> The device is named **Papouch TH2E**, not T2HE. The connector retains the name **Papouch T2HE** and works correctly with the TH2E device.

## About

### Version Info

| Range     | Key Features     | Based on     | System Impact     |
|-----------|------------------|--------------|-------------------|
| 1.0.0.x   | Initial version. | -            | -                 |

### Product Info

| Range     | Supported Firmware          |
|-----------|-----------------------------|
| 1.0.0.x   | 6.7/17 (created 26.02.2019) |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy.*

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element has the following data pages:

- **General**: Contains the measured values of temperature, humidity and dew point.
- **Extreme Values**: Displays the lowest and highest values that have been measured since the last reset or since the element was created. The information is displayed in a table with the values and the times those values were detected. The maximum and minimum limits defined by the user are also displayed.
