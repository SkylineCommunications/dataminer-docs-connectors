---
uid: Connector_help_Ateme_AMS
---

# Ateme AMS

The Ateme AMS connector gets the data of a remote DataMiner System through the HTTP SOAP API.

The connector supports polling of a limited number of external connectors in order to create DVE elements.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | V1                     |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -       | - [Ateme AMS - Ateme Titan Live](xref:Connector_help_Ateme_AMS_-_Ateme_Titan_Live)<br>- [Ateme AMS - Ateme Titan Mux](xref:Connector_help_Ateme_AMS_-_Ateme_Titan_Mux)<br>- [Ateme AMS - CISCO Manager](xref:Connector_help_Ateme_AMS_-_CISCO_Manager)<br>- [Ateme AMS - Microsoft Platform](xref:Connector_help_Ateme_AMS_-_Microsoft_Platform)<br>- [Ateme AMS - QBIT Q561](xref:Connector_help_Ateme_AMS_-_QBIT_Q561)<br>- [Ateme AMS - T-Vips CP541](xref:Connector_help_Ateme_AMS_-_T-Vips_CP541) |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: IP address of the DMS
- **IP port**: 80

### Initialization

Fill in the username and password of a user of the remote DMS.

## How to use

When you use the connector for the first time, check the **Protocols** page to see which protocols and version are supported.

The Elements page is also something you have to check to see if the DVEs are created for the elements that you want. Here you can also disable DVEs for elements that you are less interested in.
