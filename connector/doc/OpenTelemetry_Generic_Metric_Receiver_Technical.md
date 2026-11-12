---
uid: Connector_help_OpenTelemetry_Generic_Metric_Receiver_Technical
description: Technical details for the OpenTelemetry Generic Metric Receiver, which stores metrics forwarded by the OpenTelemetry Collector in a Metric Records table.
---

# OpenTelemetry Generic Metric Receiver

The OpenTelemetry Generic Metric Receiver receives metric messages forwarded by the [OpenTelemetry Collector](xref:Connector_help_OpenTelemetry_Collector) and saves them to a Metric Records table to efficiently map and view received telemetry data. It also filters the received metrics to only display required information and reduce data noise.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

No configuration is required in the element on initialization. All required configuration is done in the OpenTelemetry Collector element, in the **Metric Destinations** table on the **Match Tables** page.

> [!NOTE]
> The OpenTelemetry Collector must forward the messages using InterApp communication. Make sure you use a Collector version that supports this.

## How to Use

### Configuration

Update the **Key Regex** filter to be used when receiving messages. Only keys that match the filter will be added to the Metric Records table.

By default, all messages are added to the table, so adjust this if too much information is being processed.

### Debug

This page is only shown if **Debug** is enabled on the **Configuration** page.

When you click the **Test Messages** button, **Debug Capture Messages** displays the last 10 messages received from the OpenTelemetry Collector. You can use this to fine-tune the **Key Regex** filter to ensure that only the desired messages are stored.
