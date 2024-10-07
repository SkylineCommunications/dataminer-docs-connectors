---
uid: Connector_help_DAZN_MediaOps_VSC_Sync
---

# DAZN MediaOps VSC Sync

This connector will send HTTP POST messages to the AVOS system to keep it up to date with changes in DataMiner.

## About

### Version Info

| Range              | Features                                       | Based on | System Impact |
|--------------------|------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Handling of job updates.<br>AVOS force update. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | TBD                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

On the **Setup** page, fill in the API token.

## How to use

When a job is created, an InterApp call is performed on the connector. The connector will add this call to an internal buffer and send this request over to AVOS. When the POST fails, it will be added into the Failed Post Requests table. Every 10 seconds, this will be retried. Records in this table also have a maximum age. If they exceed this age, they are removed.

### Notes

This connector is designed to work with the DZN-UDAPI-AVOS Automation script.

In the background, there are two buffers: pending and live requests. When a pending request changes to a live request, the connector first checks if it is a patch request. If it is, the data of the patch request will be used to send a get request first, because the API expects the "LastModified" tag to be the same. For this reason, this "LastModified" value is retrieved first and then used to complete the patch request and transmit it.
