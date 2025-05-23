---
uid: Connector_help_2WCOM_DAB-4c_Technical
---

# Ateme Pilot Manager

## About

The Ateme Pilot Manager provides monitoring and control for all Ateme products and solutions deployed on premises and in a Cloud.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

In order to initialize the connector, you need to specify the following input configuration on the **General** page:

**HTTP Communication**:

- **PMF Deployment Name:** PILOT Manager Foundations portal deployment name to be use to construct the API url.
- **PMS Deployment Name:** PILOT Manager Supervision deployment name to be use to construct the API url.
- **Username:** Name of the user used in the HTTP login operation.
- **Password:** Password of the user used in the HTTP login operation.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General

On this page, you should specify the PMF deployment name and PMS deployment name  to enable the connector to construct the API URL.
Additionally, you should provide the username and password for connecting to PILOT Manager during the element initialization.

This page has one subpage:

- **Polling Settings**: Allows you to define preferred polling settings including the modules to be polled, polling interval.

### Alarms

The Alarms page displays all alarms present in the PILOT Manager. You can apply a filter to show only active alarms, which is enabled by default.

### Instances

The Instances page shows all instances in the PILOT Manager. If an instance is part of a redundancy group, you can perform a switch action to change to the backup or primary instance.

### TITAN Live Services

On this page, TITAN Live services are shown along with their inputs and outputs. For detailed information on each type of input and output, the page includes multiple subpages.

### TITAN Mux Services

On this page, TITAN Mux services are displayed along with their programs. The page also includes subpages for Mux Inputs, Outputs, and Encoders.

### Redundancy

The Redundancy page shows the redundancy groups configured.