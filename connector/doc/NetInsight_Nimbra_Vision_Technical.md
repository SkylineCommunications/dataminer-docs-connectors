---
uid: Connector_help_NetInsight_Nimbra_Vision_Technical
---

# NetInsight_Nimbra_Vision

## About

The NetInsight Nimbra Vision DataMiner connector is designed to provide management and orchestration functionalities for Nimbra MSR networks. This allows DataMiner to act as an orchestrator of orchestrators, leveraging Vision's computational and routing algorithms while maintaining a comprehensive view of the network.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *80*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

In order to initialize the connector, you need to specify the following input configuration on the **General** page:

**User credentials**:

- **Username**: Name of the user used in the HTTP login operation.
- **Password**: Password of the user used in the HTTP login operation.

**Subscriptions**:

- **Subscription Address**: The route designated for receiving subscribed alerts.
- **Subscription Port**: The IP port designated for receiving subscribed alerts.

## How to use

Once the element is successfully created, you need to specify additional details for request authentication (see [Initialization](#initialization)). This connector utilizes the HTTP protocol with subscriptions, so ensure the Nimbra Vision platform is permitted to send asynchronous alerts to your DataMiner element.

Below, you can find more detailed information about the various data pages available in the element.

### General

On this page, enter the user credentials and specify the subscription route. See [Initialization](#initialization).

#### Polling Configuration

On this page, you can review the polling configuration and **set the desired polling intervals**. The **polling refresh rate** for each endpoint is displayed here. If needed, you can disable specific endpoints. You can also request an update for these endpoints at any time by clicking the **Refresh** button.

#### Subscriptions

Nimbra Vision allows webhooks/subscriptions to be leveraged to receive updates from specific endpoints with filtering capabilities. Currently, data filtering and new endpoints cannot be added manually or on demand. If you would like to request support for additional endpoints or subscriptions, please contact Skyline Communications.

To process incoming asynchronous alerts, you can use the default subscription address or specify a different entry point. For instance, the default route address defined by the Nimbra Vision platform for communication is `http://[DMS IP ADDRESS]/NimbraVision/subscriptions`.

On the Subscriptions page, you can specify which alerts you want to subscribe to. By default, all subscriptions are disabled. You can enable them as needed.

### Managed Objects

On this page, you can view the list of networks, nodes, and circuits managed by Nimbra Vision, offering a quick overview of the ecosystem, the status of nodes, and scheduled circuits.

### Interfaces

The Interfaces page provides an overview of all interfaces, organized by port types. You can also monitor transmission capabilities and current rates.

### VA Resources

This page lists all Nimbra Video Appliance (VA) resources along with their admin, operational, and health statuses.

### Alerts

This page lists all network alarms, detailing their severity, origin, and cause.

### Web Interface

This page displays the Nimbra Vision web interface. The web interface is only accessible when the DataMiner host has network access to the Nimbra Vision platform.

## Nimbra Vision Licenses

The Nimbra Vision DataMiner connector relies on Nimbra Vision to autoroute the paths of the circuits. This requires the following functions with their respective licenses to be installed.

- **Service Provisioning**: To provision services from Nimbra Vision.
- **Northbound Provisioning**: For access to the REST APIs.
- **Scheduling**: To schedule and book resources needed by the services, e.g. ports and trunk.
capacity.
- **Autoroute**: To automatically create the path based on time, and to book available resources.

### Function Enablement

The autoroute must be enabled in the Nimbra Vision web interface for the provisioner to automatically route a path. If not, it will use whatever path the northbound application provided. If none was provided, then the network will route the channel but not create and book a path.

To enable the above-mentioned functions:

1. Install the licenses on the page *Admin* > *System Administration* > *License Details*. In the *Action* menu, select *Install*.
2. Scheduling is enabled on the page *Admin* > *Circuit Provisioning* > *Scheduling Configurations*, by setting *Enabled* to *true*.
3. Manually trigger creation of resources using the node context menu by selecting *Scheduling* > *Refresh Resources*.
4. Default circuits to autoroute on page *Admin* > *Circuit Provisioning* > *Northbound Configuration*, setting *MSR Automatic Routing: true*
