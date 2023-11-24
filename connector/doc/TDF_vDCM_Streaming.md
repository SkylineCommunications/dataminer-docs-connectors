---
uid: Connector_help_TDF_vDCM_Streaming
---

# TDF vDCM Streaming

With this connector, TDF can activate a stream from the Synamedia Digital Content Manager when this is requested by the user.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

For the element to work correctly, the files **Grille.csv** and **vDCM.csv**, which are used to load the element tables, must be placed in the protocol documents folder `C:\Skyline DataMiner\Documents\TDF vDCM Streaming`.

In addition, on the **General** page, you need to specify the device credentials.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The **General** page displays the credentials and the status of the connection with the device. There is also a button to import the CSV files (see [Initialization](#initialization)).

The **DTOM** page displays a list of the departments. You can also stop the stream there.

On the **v DCM** page, you can start and stop a particular stream.
