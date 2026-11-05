---
uid: Connector_help_EVS_XT_Access_Technical
---

# EVS XT Access

## About

The EVS XT Access connector enables comprehensive monitoring of media processing operations within XT Access. It allows broadcast operators to centrally oversee media transfer jobs between EVS production servers and external systems through a unified interface.

## Configuration

### Connections

#### HTTP Connection - IP Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

### Initialization

To enable data polling from the source, you must provide valid username and password credentials on the *General* page.

### Web Interface

The web interface is accessible only when the client machine has network connectivity to the product, and the web interface port can be configured on the *General* page.

## How to Use

Once you have provided valid credentials, the connector will automatically begin polling data and retrieve information on running and historical jobs, including general job information and detailed job destination data.
