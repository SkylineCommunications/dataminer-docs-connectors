---
uid: Connector_help_SES_Astra_CDN_Monitor
---

# SES Astra CDN Monitor

This connector displays service information, which is retrieved from an **XML file** via an **HTTP** connection.

## About

This connector processes an XML file from a server and displays the data (service information) in a tree structure.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

#### HTTP connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: URL of the destination.
- **IP port**: The IP port of the destination, port *80*.
- **Bus address**: Specify *bypassproxy.*

## Usage

### General

On this page, there is one parameter, **Refresh Rate**, which allows you to configure a refresh rate for requesting and processing the XML file. By default, the value of the parameter is set to *30 seconds*.

### Monitor

This page displays the **Monitor Table**, which contains the service information.

### Overview

This page displays the service information in a tree structure.
