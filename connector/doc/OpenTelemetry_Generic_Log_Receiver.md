---
uid: Connector_help_OpenTelemetry_Generic_Log_Receiver
---

# OpenTelemetry Generic Log Receiver

The OpenTelemetry Generic Log Receiver receives forwarded messages from the OpenTelemetry Collector and saves them to a Log Records table to efficiently map and view received telemetry data. It also filters out received logs to only display required information and reduce data noise.

## About

### Version Info

| Range   | Features        | Based on | System Impact |
|---------|-----------------|----------|---------------|
| 1.0.0.x | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

No configuration is required in the element on initialization. All the configuration required is done in the OpenTelemetry Collector element in the **Log Destinations** on the **Match Tables** page.

> [!NOTE]
> Open Telemetry Collector version 1.0.0.3 or higher is required, as the messages are forwarded using InterApp communication and previous versions do not support this.

## How to use

### Configuration

Update the **Key Regex** filter to be used when receiving messages, and only keys that match the filter will be added to the Log Records table.

By default, all messages will be added to the table, so adjust this if too much information is being processed.

### Debug

This page is only shown if **Debug** is enabled on the **Configuration** page.

When you click the **Test Messages** button, the **Debug Capture Messages** will display the last 10 messages received from the **OpenTelemetry Collector**. You can use this to fine-tune the **Key Regex** filter to ensure that only the desired messages are stored.
