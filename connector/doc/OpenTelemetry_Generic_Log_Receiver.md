---
uid: Connector_help_OpenTelemetry_Generic_Log_Receiver
---

# OpenTelemetry Generic Log Receiver

The OpenTelemetry Generic Log Receiver receives forwarded messages from the OpenTelemetry Collector and saves them to a Log Records table to efficiently map and view received telemetry data. Also filters out received logs to only display required information and reduce data noise.

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

No configuration is required on Initialization. All the configuration required is done at the OpenTelemetry Collector element in the **Log Destinations** on the **Match Tables** page.

>[!NOTE]
>Open Telemetry Collector version 1.0.0.3 or higher is required as the messages are forwarded using Interapp communication and previous versions do not support Interapp communication.

## How to use

### Configuration

Update the **Key Regex** filter to be used when receiving messages and only keys that match the filter will be added to the Log Records table. By default all messages will be added to the table, please adjust if too much information is being processed.

### Debug

This page only shows if **Debug** is enabled on the **Configuration** page.  When pressing the **Test Messages** button, the **Debug Capture Messages** will display the last 10 messages received from the **OpenTelemetry Collector**. This is to be used to fine tune the **Key Regex** filter to ensure only desired messages are stored.