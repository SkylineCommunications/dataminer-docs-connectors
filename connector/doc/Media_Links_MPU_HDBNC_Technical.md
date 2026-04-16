---
uid: Connector_help_Media_Links_MPU_HDBNC_Technical
---

# Media Links MPU HDBNC

## About

The Media Links MPU (Media Processing Unit) with HD-BNC interfaces is a hot-swappable modular card designed for the Xscend IP Media Platform. It is used to process, transport, and convert high-density video signals between traditional baseband SDI formats and IP networks (SMPTE ST 2110/2022).

This connector is used to monitor MPU modules installed in the Xscend chassis.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- IP address/host: The polling IP or URL of the destination.
- IP port: The IP port of the destination.

### Initialization

For the connector to start polling data from the data source, you need to provide the user name and password credentials. In addition, on the **General** page, you will need to set the slot index of the MPU module.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

By setting the **Display Alarms** parameter on the **Alarms** page, you can choose to display all alarms or only active alarms.
