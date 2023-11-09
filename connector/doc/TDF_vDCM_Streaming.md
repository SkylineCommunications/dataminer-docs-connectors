---
uid: Connector_help_TDF_vDCM_Streaming
---

# TDF vDCM Streaming

This connector enables TDF to activate, on user request, a stream from the device Synamedia Digital Content Manager.
## About

### Version Info
| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x \[SLC Main\] | Initial Version  | \-           | \-                |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | \-                     |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | \-                    | \-                      |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination. (default: *443*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]


### Initialization

In order for the element to work, the csv files (Grille.csv  and vDCM.csv) used to load the element tables must be placed in the protocol documents folder "C:\Skyline DataMiner\Documents\TDF vDCM Streaming".
The user needs to set the device credentials in the General page.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The **General** page displays the credentials and the connection status of the element with the device. There is also a button to import the csv files.
The **DTOM** page displays the list of departments and the possibility to stop the Stream  and in the **v DCM** page the user can start and stop a particular stream.
