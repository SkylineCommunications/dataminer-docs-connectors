---
uid: Connector_help_Asentria_SiteBoss_360
---

# Asentria SiteBoss 360

## About

This is a DataMiner connector for the **Asentria SiteBoss 360**. Using this connector, you can monitor and configure the event sensor points connected to the device.

### Key Features

- **Alarm monitoring of the event sensor points**: Each alarm triggered in the event sensor points can be monitored in real time.
- **Alarm configuration of the event sensor points**: Each type of supported event sensor point is accompanied by a configuration table that allows you to set thresholds, severities, and unique descriptions for the sensor values to trigger alarms.

## Use Cases

### Event Sensor Points Monitoring and Configuration

**Challenge**: The **Asentria SiteBoss 360** returns all event sensor points in a single table, regardless of type. Configuration options are not clearly explained.

**Solution**: With this connector, each type of event sensor point, i.e. analog inputs, contact closures, humidity sensors, outputs, and temperature sensors, has its own dedicated page to better categorize the different sensors and their states. The configuration table is also enhanced with better explanations to aid in alarm configuration.

## Technical Information

### Prerequisites

- **DataMiner version 10.3 or higher** is required.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Asentria_SiteBoss_360_Technical).
