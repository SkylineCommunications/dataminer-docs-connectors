---
uid: Connector_help_RME_Sensors_IP_TH_Sensor
description: Monitor temperature and humidity from RME Sensors IP TH sensors over HTTP, including minimum and maximum readings and device information.
---

# RME Sensors IP TH Sensor

## About

The **RME Sensors IP TH Sensor** connector integrates RME Sensors IP-based temperature and humidity (TH) sensors into DataMiner. It polls the sensor over HTTP and makes the current climate readings and device information available in DataMiner, so that you can keep an eye on the environmental conditions in equipment rooms, racks, and other sensitive locations alongside the equipment itself.

## Key Features

- **Temperature monitoring**: Track the current temperature (°C) together with the minimum and maximum values registered by the sensor.

- **Humidity monitoring**: Track the current relative humidity (%) together with the minimum and maximum values registered by the sensor.

- **Device information**: View the sensor model, firmware version, and MAC address, as well as the configured PRTG output and sensor type.

## Use Cases

### Climate monitoring in equipment rooms

**Challenge**: Overheating or excessive humidity in server rooms and racks leads to equipment failure, but the conditions are often only noticed once damage has been done.

**Solution**: Place IP TH sensors in critical locations and monitor them with this connector in the same DataMiner System as the equipment they protect.

**Benefit**: Adverse climate conditions are detected early and can be correlated with the health of the surrounding equipment.

## Technical Reference

### Prerequisites

- DataMiner **10.3.0 (build 12752)** or higher.
- Network access from the DataMiner Agent to the sensor's HTTP(S) interface (default port *443*).

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the sensor.
- **IP port**: The IP port of the sensor (default: *443*).
- **Device address**: *bypassproxy*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.
