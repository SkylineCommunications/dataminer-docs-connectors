---
uid: Connector_help_ATT_Channel_Manager
---

# ATT Channel Manager

In order to manage channels in the **ATT DFW** ecosystem, a DataMiner solution is required which can ingest and store channel data, and automatically initiates the generation of monitoring objects for those channels, known as DataMiner services.

## About

The channel manager solution comes in the form of a single instance of a DataMiner Application that communicates with the **ATT AVCM API** to retrieve the channel information.

### Version Info

| Range              | Key Features                                                                     | Based on | System Impact |
|--------------------|----------------------------------------------------------------------------------|----------|---------------|
| 3.0.0.x [SLC Main] | - AVCM Channels retrieved<br>- AVCM Channels Validation<br>- HTTP Status counter | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 3.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

- The **AVCM Pods Mapping** table allows you to set the **Compression Element** either manually or automatically. If it is set automatically, the connector will check in the **Protocols** table and find the element doing a mapping between the **Pod Service** column and the **Pod Name** property.

- The **Custom Channels** table can be imported using a CSV file with the proper format.

- The **Protocols** table allows you to manually enter **Compression Element** protocols.
