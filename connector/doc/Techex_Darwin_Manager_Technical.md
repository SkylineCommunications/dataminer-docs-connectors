---
uid: Connector_help_Techex_Darwin_Manager_Technical
---

# Techex Darwin Manager

## About

**Techex Darwin** is a cloud-native media processing platform used to process, transport, monitor, and distribute live video workflows.

The **Techex Darwin Manager** connector enables seamless integration between DataMiner and Techex Darwin video processing systems. This connector provides comprehensive monitoring and control capabilities for Darwin's modular video processing platform, allowing broadcast and media operations to manage complex video workflows through DataMiner's unified interface.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- IP address/host: The polling IP or URL of the destination.
- IP port: The IP port of the destination.
- Bus address: If the proxy server has to be bypassed, specify *bypassproxy*.

### Initialization

For the connector to start polling data from the Darwin Manager API, you need to provide authentication credentials:

1. After you have created an element, navigate to the **General** page.
1. Enter the username in the **Username** field.
1. Enter the password in the **Password** field (stored encrypted).

The connector will begin polling once valid credentials are configured. All polling groups require authentication and will be skipped if credentials are empty.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

### Automation Scripts

The connector launches an interactive automation script to instantiate blueprints. For the blueprint instantiation feature to work, you need to install the [Techex Darwin Blueprint Instantiate](https://github.com/SkylineCommunications/SLC-AS-TechexDarwin) automation script on your DataMiner system.

## How to Use

To instantiate a blueprint:

1. Go to the **Blueprints** table on the **Blueprints** page.
1. Click the **Instantiate** button for the desired blueprint.
   An interactive window will pop up.
1. Fill all the relevant fields.
1. Click the **Instantiate** button on the second page.
