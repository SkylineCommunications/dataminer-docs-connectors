---
uid: Connector_help_Waterkotte_Heatpump_Technical
---

# Waterkotte Heatpump

## About

The Waterkotte Heatpump connector enables monitoring of the heatpump of Waterkotte devices via modbus. It provides users with access to real-time data directly within DataMiner.

## Configuration

### Connections

#### Serial Connection - IP Connection

This connector uses an serial connection and requires the following input during element creation:

- **IP address/host**: The IP address linked to the modbus of the.
- **IP port**: The port used to connect to the modbus. Default is 503.

### Initialization

Waterkotte is accessible by modbus, so the connector will begin polling from the moment the element is started up.

## How to Use

Once an element is configured, the connector automatically starts polling data from the Waterkotte Heatpump API.
