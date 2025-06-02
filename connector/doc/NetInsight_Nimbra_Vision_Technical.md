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

- **Username:** Name of the user used in the HTTP login operation.
- **Password:** Password of the user used in the HTTP login operation.

**Subscriptions**:

- **Subscription Address:** The route designeted for receiving for receiving subscribed alerts.
- **Subscription Port:** The IP port designated for receiving subscribed alerts.

## How to use
Once the element is successfully created, you need to specify additional details. Navigate to the General page to set your Username and Password for request authentication. This connector utilizes the HTTP protocol with Subscriptions, so ensure the Nimbra Vision platform is permitted to send asynchronous alerts to your DataMiner element (see [Initialization](#initialization)).

Below, you can find more detailed information about the various data pages available in the element.

### General
On this page, enter the user credentials and specify the subscription route. See [Initialization](#initialization).

#### Polling Configuration
On this page, users can review the Polling Configuration and set the desired polling intervals. The polling refresh rate for each endpoint is displayed here. If needed, you can disable specific endpoints. You can also request an update for these endpoints at any time by clicking the 'Refresh' button.

#### Subscriptions
Nimbra Vision allows us to leverage Webhooks/subscriptions to receive updates from specific endpoints with filtering capabilities. Currently, data filtering and new endpoints cannot be added manually or on-demand. For support with additional endpoints or subscriptions, please contact Skyline team members for evaluation.

To process incoming asynchronous alerts, you can use the default Subscription Address or specify a different entry point. For instance, the default route address defined by the Nimbra Vision platform for communication is: ```http://[DMS IP ADDRESS]/NimbraVision/subscriptions```.

On this page, you can specify which alerts you want to subscribe to. By default, all subscriptions are disabled and can be enabled as needed.

### Managed Objects
On this page, users can view the list of networks, nodes, and circuits managed by Nimbra Vision, offering a quick overview of the ecosystem, the status of nodes, and scheduled circuits.

### Interfaces
The Interfaces page provides an overview of all interfaces, organized by port types. Users can also monitor transmission capabilities and current rates.

### VA Resources
This page lists all Nimbra Video Appliance (VA) resources along with their admin, operational, and health statuses.

### Alerts
This page lists all network alarms, detailing their severity, origin, and cause.

### Web Interface

This page displays the TXCore web interface. The web interface is only accessible when the DataMiner host has network access to the TXCore platform.

## Nimbra Vision Licenses
The Nimbra Vision DataMiner connector relies on Nimbra Vision to autoroute the paths of the circuits. This requires the following functions with its respective licenses to be installed.

- **Service Provisioning**: to provision services from Nimbra Vision
- **Northbound Provisioning**: access the REST APIs
- **Scheduling**: to schedule and book resources needed by the services, e.g., ports and trunk
capacity.
- **Autoroute**: to automatically create the path based on time, and book and available resources.

### Function Enablement
The autoroute must be enabled for the provisioner to automatically route a path. If not, then it will use whatever path the northbound application provided. If none was provided, then the network will route the channel but not create and book a path. 

To enable above mentioned functions:

- Install the licenses on page *Admin > System Administration > License Details*. In *Action* menu, select *Install...*.
- Scheduling is enabled on page *Admin > Circuit Provisioning > Scheduling Configurations*, setting *Enabled: true*
- Manually trigger creation of resources using the node context menu: *Scheduling > Refresh Resources...*. 
- Default circuits to autoroute on page *Admin > Circuit Provisioning > Northbound Configuration*, setting *MSR Automatic Routing: true*