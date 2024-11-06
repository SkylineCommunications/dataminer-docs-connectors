---
uid: Connector_help_OpenTelemetry_Collector
---

# OpenTelemetry Collector

The OpenTelemetry Collector is a listener that receives/buffers messages from the OTEL Collector. It matches these messages via mapping tables and then forwards them to a specified OpenTelemetry Generic Log Receiver element.

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

When the element has been created, on the **General** page, configure the **Authorization Token** and **one of the URLs** for the listener to match incoming messages.

You will also need to add a row to one of the [matching tables](#match-tables).

## How to use

### General

This page contains the basic configuration parameters such as **Authorization Token**, **OT Logs URL**, **OT Traces URL**, **OT Metrics URL**, and the **HTTP Status Code**. It also contains a page button to the **Statistics** page, which shows various message statistics.

### Match Tables

This page contains the **Log**, **Metric**, and **Trace** destination tables, where you can add a row to filter/match incoming messages. By default, an asterisk (`*`) is added, which represents a wildcard.

### Debug

This page contains the **Message** parameter, which shows the current message from the device.
