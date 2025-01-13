---
uid: Connector_help_Grass_Valley_AMPP_Manager
---

# Grass Valley AMPP Manager

The Grass Valley Agile Media Processing Platform (GVAMPP) connector will retrieve a list of existing workloads to be managed/configured.

## About

A smart serial connection is needed to listen to incoming messages, and an additional 2 HTTP connections are needed: one for the GVAMPP and one for the SignalR Forwarder

### Version Info

| Range   | Description     | DCF Integration | Cassandra Compliant |
|---------|-----------------|-----------------|---------------------|
| 1.0.0.x | Initial version | No              | Yes                 |
### Product Info

| Range   | Supported Firmware Version |
|---------|----------------------------|
| 1.0.0.x | xxx                        |

## Installation and configuration

### Connections
#### IP Connection - Main

This connector uses a smart serial connection by IP to act as listener

- **IP address/host**: The polling IP or URL of the destination by default, any
- **IP port**: The IP port of the destination by default, 5001

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

## Usage

Once created, the element can be used immediately.

### General

This page contains general configuration parameters: API Key, Last Login Time, and Token Expiration. Default Token Expiration is 24 hours, but a new token will automatically be requested on API Key change and every 12 hours.

### Application Types

Here you will find the voltage the application types table.

### Workloads

Here you will find the workloads table as well as a button to refresh the workloads. Each row contains several buttons/toggle buttons: 
* Get State - sends a Get State POST Command
* Disable Get State - sends a Disable Get State DELETE Command
* Start - sends a Start Workload POST Command 
* Stop - sends a Stop Workload POST Command
* Refresh State on Restart - Sends a Get State command after restart of element. 

### Fabrics and Nodes

Here you will find the Fabrics and Nodes tables as well as a button to refresh them.

### Snapshots

Here you will find the Snapshots table as well as a button to refresh the snapshots. Each row contains several buttons/toggle buttons:
* Start - sends a Start Snapshot POST Command 
* Stop - sends a Stop Snapshot POST Command
* Restore Workloads After Start - restores the workload on element restart

### Debug

This page contains the current listener message as well as the response to AMPP

### Web Inteface

Access to the Web GUI is found here.