---
uid: Connector_help_2WCOM_DAB-4c_Technical
---

# Ateme Pilot Manager

## About

The Ateme Pilot Manager provides comprehensive monitoring and control for Ateme products and solutions, whether deployed on-premises or in the cloud. It offers intuitive operational views for real-time monitoring and service delivery control, with automatic failure detection and recovery. This guarantees continuous delivery and minimal service disruption. At the time of this writing, Ateme Pilot Manager supports Titan Live, Titan Edge and Titan Mux products.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

On the first startup, to initialize the connector, you need to specify the following input configuration on the **General** page:

- **PMF Deployment Name:** Pilot Manager Foundations portal deployment name to be use to construct the API url.
- **PMS Deployment Name:** Pilot Manager Supervision deployment name to be use to construct the API url.
- **Username:** Name of the user used in the HTTP login operation.
- **Password:** Password of the user used in the HTTP login operation.

> [!Important]
> To identify the PMF and PMS, access the Pilot Manager portal webpage. In the URL, you can find the PMF and PMS before and after the word 'applications' in the path, respectively. Example, `https://<IP>/<PMF>/applications/<PMS>`

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General

On this page, you should specify the PMF deployment name and PMS deployment name  to enable the connector to construct the API URL.
Additionally, you should provide the username and password for connecting to v Manager during the element initialization.

This page has one subpage:

- **Polling Settings**: Allows you to define preferred polling settings including the modules to be polled, polling interval.

### Alarms

The Alarms page displays all alarms present in the PILOT Manager. By default, **a filter is applied to show only active alarms**. When this filter is disabled, alarms from the last 24 hours are displayed.

### Instances

The Instances page shows all instances in the Pilot Manager. If an instance is part of a redundancy group, you can perform a switch action to change to the backup or primary instance.

### Titan Live Services

On this page, Titan Live services are shown along with their inputs and outputs. For detailed information on each type of input and output, the page includes multiple subpages.

### Titan Mux Services

On this page, Titan Mux services are displayed along with their programs. The page also includes subpages for Mux Inputs, Outputs, and Encoders.

### Redundancy

The Redundancy page shows the redundancy groups configured.