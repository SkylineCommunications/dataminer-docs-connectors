---
uid: Connector_help_Zaptec_Platform_Technical
---

# Zaptec Platform

## About

The Zaptec Platform connector enables monitoring of electric vehicle (EV) charging operations within the Zaptec ecosystem. It allows users to oversee and manage EV charging activities through a centralized interface.

## Configuration

### Connections

#### HTTP Connection - IP Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The URL of the Zaptec Platform API.
- **IP port**: The port used to connect to the Zaptec Platform API.

### Initialization

To enable data polling from the source, valid username and password credentials must be provided on the *Element Settings* page.

## How to Use

Once valid credentials have been provided, the connector will automatically begin polling data from the Zaptec cloud API, retrieving information on installations and chargers, including charger status and session activity.
Data polling configuration table is available to adjust the polling intervals and control which data sets are retrieved, allowing operators to balance data retrival against API fair use limits.