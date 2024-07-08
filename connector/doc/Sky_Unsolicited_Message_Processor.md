---
uid: Connector_help_Sky_Unsolicited_Message_Processor
---

# Sky Unsolicited Message Processor

The connector manages incoming data received via InterApp. Data is then processed according to preconfigured rules, and the result is displayed in a table for alerting purposes.

## About

### Version Info

| Range              | Key Features     | Based on    | System Impact |
|--------------------|------------------|-------------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -           | -             |

### Product Info

| Range     | Supported Firmware |
|-----------|--------------------|
| 1.0.0.x   | -                  |

### System Info

| Range     | DCF Integration | Cassandra Compliant| Linked Components | Exported Components |
|-----------|-----------------|--------------------|-------------------|---------------------|
| 1.0.0.x   | No              | Yes                | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

No extra configuration is needed.

### Automation Scripts

This connector can be used with a User Defined API (**SIT-UDAPI-UnsolicitedMessageProcessor**) that receives events from the OBM device. The UDAPI then sends the event information to the connector via InterApp.

## How to use

### General

On this page, you can define the policies to apply to the incoming events. These policies can be added via a JSON file or manually via the context menu.

### Alarms

This page displays an overview of the Alarms generate by the incoming events.

### Dimissed Events

On this page, you can view the Events that have been dimissed by the policies set up.

