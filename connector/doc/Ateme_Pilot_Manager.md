---
uid: Connector_help_Ateme_Pilot_Manager
---

# Ateme Pilot Manager

## About

The Ateme Pilot Manager provides comprehensive monitoring and control for Ateme products and solutions, whether deployed on-premises or in the cloud. It offers intuitive operational views for real-time monitoring and service delivery control, with automatic failure detection and recovery. This guarantees continuous delivery and minimal service disruption. At present, Ateme Pilot Manager supports Titan Live, Titan Edge, and Titan Mux products.

### Product Info

| Range | Supported Firmware |
| -- | -- |
| 1.0.0.x | 4.0.0 |

## Key Features

- **Centralized monitoring**: Monitor all your Ateme products in one place.
- **Redundancy**: Ensures continuous delivery and minimal service disruption through automatic failure detection and recovery.

## Configuration

### HTTP Connection

When you create a DataMiner element using this connector in DataMiner Cube, you will need to specify the following details for the HTTP connection:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

On the first startup, to initialize the element, you need to specify the following input configuration on the **General** page of the element:

- **PMF Deployment Name**: Pilot Manager Foundations portal deployment name to be used to construct the API URL.
- **PMS Deployment Name**: Pilot Manager Supervision deployment name to be used to construct the API URL.
- **Username**: Name of the user used in the HTTP login operation.
- **Password**: Password of the user used in the HTTP login operation.

> [!IMPORTANT]
> To identify the PMF and PMS, access the Pilot Manager portal webpage. In the URL, you can find the PMF and PMS before and after the word "applications" in the path, respectively. Example: `https://<IP>/<PMF>/applications/<PMS>`.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General

On this page, you should specify the PMF deployment name and PMS deployment name to enable the connector to construct the API URL.

Additionally, you should provide the username and password for connecting to the Pilot Manager during the element initialization.

This page has a **Polling Settings** subpage, where you can define preferred polling settings, including the modules to be polled and the polling interval.

### Alarms

The Alarms page displays all alarms present in the Pilot Manager. By default, **a filter is applied to show only active alarms**. When this filter is disabled, alarms from the last 24 hours are displayed.

### Instances

The Instances page shows all instances in the Pilot Manager. If an instance is part of a redundancy group, you can perform a switch action to change to the backup or primary instance.

### Titan Live Services

On this page, Titan Live services are shown along with their inputs and outputs. For detailed information on each type of input and output, the page includes multiple subpages.

### Titan Mux Services

On this page, Titan Mux services are displayed along with their programs. The page also includes subpages for Mux Inputs, Outputs, and Encoders.

### Redundancy

The Redundancy page shows the configured redundancy groups.
