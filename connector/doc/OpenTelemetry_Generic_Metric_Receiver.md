---
uid: Connector_help_OpenTelemetry_Generic_Metric_Receiver
description: Capture and view OpenTelemetry metrics in DataMiner. Receive metrics forwarded by the OpenTelemetry Collector and filter them to keep only what matters.
---

# OpenTelemetry Generic Metric Receiver

## About

The OpenTelemetry Generic Metric Receiver is a DataMiner connector that receives metrics forwarded by the [OpenTelemetry Collector](xref:Connector_help_OpenTelemetry_Collector). It stores them in a clear, easy-to-browse table so you can view telemetry data from any OpenTelemetry-enabled source in DataMiner.

## Key Features

- **Metric overview**: Stores received metrics in a Metric Records table, so you can easily map and view telemetry data.

- **Noise reduction**: Filters the received metrics so that only the information you need is displayed.

- **Easy setup**: Does not require any configuration on the element itself. Metrics are routed to the connector from the OpenTelemetry Collector.

- **Troubleshooting support**: Lets you inspect the most recent messages received, so you can fine-tune your filter.

## Use Cases

### Unified Telemetry Visibility

**Challenge**: Applications and infrastructure that emit OpenTelemetry metrics produce large volumes of data, which makes it hard to see what is relevant.

**Solution**: The OpenTelemetry Generic Metric Receiver collects the metrics forwarded by the OpenTelemetry Collector and keeps only those that match your filter.

**Benefit**: You get a focused view of your telemetry data inside DataMiner, without unnecessary data noise.

## Technical Reference

### Prerequisites

Make sure an OpenTelemetry Collector element is available in your DataMiner System and that it is configured to forward metrics to this element.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_OpenTelemetry_Generic_Metric_Receiver_Technical).
