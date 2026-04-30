---
uid: Connector_help_Paneda_DAB_Head-End_Technical
---

# Paneda DAB Head-End

## About

This connector retrieves the status information from four URLs (General System, Devices, Audio Services, and Data Services) for each provider configured in the system.

The data returned by the calls for each provider consists of data specific for that provider as well as general data on the overall system, which is identical for all the providers. The connector only displays the general data once, separately from the data that is unique for each provider. As such, if no provider is mentioned, this means the data relates to the overall system.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: 443

#### SNMP Connection - SNMP

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

On the **General** page, the correct authorization token must be specified with the **Paneda Access Token** parameter.

## How to Use

This connector retrieves information from the Paneda via HTTPS for each provider configured on the device.

The configured providers are retrieved from an SNMP table. The access token needs to be configured for each provider, otherwise no access will be provided.

The web interface is not available in the element. You can access it outside DataMiner Cube using Chrome.
