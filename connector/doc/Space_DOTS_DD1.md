---
uid: Connector_help_Space_DOTS_DD1
---
# Space DOTS DD1

## About

The **Space DOTS DD1** connector provides operational visibility into Space DOTS DD1 spacecraft telemetry exposed over HTTP APIs.

It helps operators monitor platform health, authentication state, orbital position, power/radiation behavior, and thermal sensor conditions from a single DataMiner element.

## Key Features

- Monitors **public and protected health endpoints** to validate service availability.
- Tracks **authentication status** and token lifecycle for secured API access.
- Ingests **raw telemetry frames** and exposes actionable monitoring parameters.
- Provides **position metrics** such as latitude, longitude, altitude, and velocity.
- Exposes **power and radiation telemetry** per dataset, including voltage/current channels and dosimeter values.
- Provides **thermal analytics** with summary min/max/average temperatures and per-sensor PT1000/magnetometer readings.
- Supports **operator labeling** for PT1000 and magnetometer sensors to improve readability.

## Monitored Data Highlights

- Service health status and timestamp
- Authentication success/failure
- Satellite position and recency of telemetry
- Power bus voltage/current and aggregate totals
- Dosimeter dose rate, count, and temperature
- Thermal summary statistics and per-sensor temperatures
- Magnetometer field components (X/Y/Z)

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Space_DOTS_DD1_Technical).
