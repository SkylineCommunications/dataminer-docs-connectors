---
uid: Connector_help_DYN_Live_Production_Manager_Technical
---

# DYN Live Production Manager

## About

This is a custom DataMiner connector for DYN. The connector is used to visualize live production events.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The polling IP of the destination.
- **IP port**: The IP port of the destination (default: *443*).

## How to Use

The connector uses API calls to request information from the DYN server.

1. Provide API key.
2. Enter the period for which you want to view live productions.  