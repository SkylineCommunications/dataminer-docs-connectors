---
uid: Connector_help_Inmarsat_Gateway
---

# Inmarsat Gateway

Inmarsat Gateway is an implementation of the iDirect API provided by Inmarsat. This connector is mainly used to monitor data depending on the user credentials.

## About

This connector uses the **HTTP** protocol to create sessions and request data from the server. The data is received in a JSON format which is then parsed and displayed.

Note: The connector only polls data for terminals that have been assigned to the protocol by the **Inmarsat Gateway Director protocol**.

This connector can be configured to request additional data via SSH.

This connector will export different connectors based on the retrieved data. A list can be found in the section "Exported Connectors".

### Version Info

| Range   | Description                                                   | DCF Integration | Cassandra Compliant |
|---------|---------------------------------------------------------------|-----------------|---------------------|
| 1.0.0.x | Initial version                                               | No              | Yes                 |
| 1.0.1.x | Added second connection to the connector                      | No              | Yes                 |
| 2.0.0.x | Master/slave functionality with the Inmarsat Gateway Director | No              | Yes                 |
| 2.1.0.x | Support for the new Inmarsat API                              | No              | Yes                 |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | API ICD V2.07               |
| 1.0.1.x          | API ICD V2.07               |
| 2.0.0.x          | API ICD V2.07               |
| 2.1.0.x          | API SDD V0.8                |

### Exported connectors

| Exported Connector          | Description |
|-----------------------------|-------------|
| Inmarsat Gateway - Terminal | Terminal    |

## Configuration

### Connections - Range 1.0.0.x to 2.0.0.x

#### HTTP main connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: `https://api.inmarsat.com`
- **IP port**: 443
- **Bus address**: byPassProxy

#### Serial SSH connection

This connector also uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:

- Interface connection:

  - **IP address/host**: 127.0.0.1
  - **IP port**: 22

### Connections - Range 2.0.0.x

#### HTTP main connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: `https://inmarsat-prod.apigee.net`
- **IP port**: 443
- **Bus address**: byPassProxy

## Usage (versions 1.0.0.x to 2.0.0.x)

### Terminals

This page contains a **DVE table** with an overview of all available **terminals**. In this table, you can manually enter a **custom IP address** for each terminal. These IP addresses will be used to poll the device via **SSH** for extra data if this option is enabled.

In addition, it is possible to **enable/disable the automatic removal of DVE elements** for terminals that have been removed.

### Metric Overview

This page contains a table with all the **statistics** that can be polled for all the object types.

### Authentication

This page is used to insert credentials for the **Inmarsat Gateway API** as well as for the **SSH** sessions. The **Connection Status** parameter indicates the status of the main (HTTP) connection.

To request information from the **Inmarsat Gateway API**, the following information must be filled in:

- **API Key**
- **API Username**
- **API Password**

To request information from the terminal devices via **SSH**, the following information must be filled in:

- **SSH Username**
- **SSH Password**

### Configuration

This page can be used to configure the **Maintenance Method** for events, i.e. depending on the **number** **of days**, depending on the **number** **of lines** or **none**. The **last update timestamp** of the events is also displayed here.

Finally, you can also **enable/disable** the **SSH** communication by toggling the **NSD Info Retrieval** toggle button.

## Usage (version 2.0.1.x)

### General

This page displays an overview of the element information. It contains information about the gateway manager and the event handler.

The **event handler** allows you to set a maximum number of events to be kept, or to limit the events table to a certain number of days.

### Terminals

This page contains a **DVE table** with an overview of all available **terminals**. It also allows you to **enable/disable the automatic removal of DVE elements** for terminals that have been removed.

### Authentication

This page is used to insert credentials for the **Inmarsat Gateway API**. The **Connection Status** parameter indicates the status of the main (HTTP) connection.

To request information from the **Inmarsat Gateway API**, fill in the **API Client ID** and **API Client Secret** and click **Get Access Token** to request access to the API.
