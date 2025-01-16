---
uid: Connector_help_Grass_Valley_AMPP_Manager
---

# Grass Valley AMPP Manager

The Grass Valley Agile Media Processing Platform (GVAMPP) connector will retrieve a list of existing workloads to be managed/configured.

A smart-serial connection is needed to listen to incoming messages, and an additional two HTTP connections are needed, one for the GVAMPP and one for the SignalR Forwarder.

## Configuration

### Connections

#### IP Connection - Main

This connector uses a smart-serial connection by IP to act as listener.

- **IP address/host**: The polling IP or URL of the destination (default: *any*).
- **IP port**: The IP port of the destination (default: *5001*).

#### HTTP Connection - GVAMPP

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

#### HTTP Connection - SignalR Forwarder

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## Usage

### General

This page contains general configuration parameters: API Key, Last Login Time, and Token Expiration. Token Expiration is by default set to 24 hours, but a new token will automatically be requested whenever there is an API key change and every 12 hours.

### Application Types

Here you will find the application types table.

### Workloads

Here you will find the workloads table as well as a button to refresh the workloads. Each row contains several buttons/toggle buttons:

- **Get State**: Sends a Get State POST command.
- **Disable Get State**: Sends a Disable Get State DELETE command.
- **Start**: Sends a Start Workload POST command.
- **Stop**: Sends a Stop Workload POST command.
- **Refresh State on Restart**: Sends a Get State command after a restart of the element.

### Fabrics and Nodes

Here you will find the fabrics and nodes tables as well as a button to refresh them.

### Snapshots

Here you will find the snapshots table as well as a button to refresh the snapshots. Each row contains several buttons/toggle buttons:

- **Start**: Sends a Start Snapshot POST command.
- **Stop**: Sends a Stop Snapshot POST command.
- **Restore Workloads After Start**: Restores the workload on element restart.

### Debug

This page contains the current listener message as well as the response to AMPP.
