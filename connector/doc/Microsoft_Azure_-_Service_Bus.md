---
uid: Connector_help_Microsoft_Azure_-_Service_Bus
---

# Microsoft Azure - Service Bus

Azure Service Bus is an asynchronous messaging cloud platform that makes it possible to send data between decoupled systems.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware          |
|-----------|-----------------------------|
| 1.0.0.x   | REST-API version 2021-05-01 |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components                                                     | Exported Components |
|---------|-----------------|---------------------|-----------------------------------------------------------------------|---------------------|
| 1.0.0.x | No              | Yes                 | [Microsoft Azure Cloud Platform](xref:Connector_help_Microsoft_Azure) | -                   |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection. However, it requires no input from the user, as this connector is automatically created by the **Microsoft Azure Cloud Platform**.

## How to use

The connector requires no user input. The metrics that are polled for this resource type element are displayed on the **Metrics** page.

### Polling Configuration

Enabling or disabling polling of metrics can be done on the **Configuration** page. Polling of these metric has a direct financial impact.

On the **General** page, you can configure the **Polling Interval** for the metrics. This same page also displays the scope (Subscription and Resource Group) that this resource type element belongs to.

### Query Filter

Also on the **General** page, you can configure the **Query Filter**. This filter is used to reduce the set of metric data returned.

This is how the filter works, based on an example where the metric contains the metadata A, B, and C:

- To return all time series of C where A = a1 and B = b1 or b2:

  `filter=A eq 'a1' and B eq 'b1' or B eq 'b2' and C eq '*'`

  Invalid variant:

  `filter=A eq 'a1' and B eq 'b1' and C eq '*' or B = 'b2'`

  This is invalid because the logical "or" operator cannot separate two different metadata names.

- To return all time series where A = a1, B = b1 and C = c1:

  `filter=A eq 'a1' and B eq 'b1' and C eq 'c1'`

- To return all time series where A = a1:

  `filter=A eq 'a1' and B eq '' and C eq ''`

- If multiple entities are present in same namespace filter can be utilized to use only one

  `filter=entityname eq 'prod'`

  The following metrics support filtering by EntityName:

  - Abandoned Messages
  - Active Messages
  - Completed Messages
  - Connections Closed
  - Connections Opened
  - Dead Lettered Messages
  - Incoming Messages
  - Incoming Requests
  - Messages
  - Outgoing Messages
  - Scheduled Messages
  - Server Errors
  - Server Send Latency
  - Successful Requests
  - Throttled Requests
  - User Errors

If the specified filter does not use the correct format, or if the metric does not support a filter of that type, then the filter will not be applied.

## Notes

This connector is intended to be used together with the **Microsoft Azure Cloud Platform** connector. Without this manager connector, the connector will not work, as the authentication to the Azure Cloud Platform is done via the manager connector.
