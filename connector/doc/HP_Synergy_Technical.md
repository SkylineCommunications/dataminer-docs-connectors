---
uid: Connector_help_HP_Synergy_Technical
---

# HP Synergy

## About

The HP Synergy connector enables DataMiner integration and monitoring of HP Synergy devices via the HP OneView management platform. The connector uses the RESTful API to communicate with the device.

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

### Initialization

On the **General** page, specify the **User**, **Password**, and **Domain** credentials needed to authenticate to the HP OneView management platform. Polling will not start until valid credentials are provided.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General

On this page, you can enter the credentials (**User**, **Password**, and **Domain**) to authenticate to the HP Synergy device. If the credentials are correct, the **Connection Status** parameter will indicate the value *Connected*, and the element will start polling data from the device.

The page also displays the current API version information (**Current Version**, **Minimum Version**, **API Version**, and **API Validity**).

### Enclosures

This page displays information about enclosures in the **Enclosure Table**, **Enclosure Group Table**, and **Logical Enclosure Table**.

### Servers

This page displays information about servers in the **Server Hardware Table**, **Server Hardware Type Table**, **Server Profile Table**, and **Server Profile Template Table**.

### Networks

This page displays information about network resources in the **Connection Table**, **Connection Template Table**, **Ethernet Network Table**, **Fabric Table**, **FC Network Table**, **FCoE Network Table**, and **Network Set Table**.

### Interconnect

This page displays information about interconnects in the **Interconnect Table**, **Interconnect Type Table**, **Internal Link Set Table**, **Logical Downlink Table**, **Logical Interconnect Group Table**, **Logical Interconnect Table**, **Uplink Port Table**, and **Uplink Set Table**.

### Storage

This page displays information about storage resources in the **Managed SAN Table**, **Storage Pool Table**, **Storage System Table**, **Storage Volume Table**, **Storage Volume Attachment Table**, and **Storage Volume Set Table**.

### Facilities

This page displays information about the physical infrastructure in the **Datacenter Table**, **Power Device Table**, **Rack Table**, and **Rack Manager Table**.

### Devices

This page displays information about device bays in the **Device Bay Table**, **Fan Bay Table**, **Manager Bay Table**, and **Power Supply Bay Table**.

### Drive Enclosure

This page displays information about drive enclosures in the **Drive Enclosure Table**, **Drive Bay Table**, and **IO Adapters Table**.

### Server Profile Storage

This page displays storage configuration for server profiles in the **Local Storage Controller Table**, **Logical Drive Table**, **Logical JBOD Table**, and **SAN Volume Attachment Table**.

### Alerts

This page displays alert information in the **Alert Table** and event information in the **Event Table**. The **Events Retrieve Time** and **Events Retrieved for Alert(s)** parameters allow you to control event retrieval.

### Tasks

This page displays task information in the **Task Table**. Via the **Tasks Filter** subpage, you can configure filters for the task retrieval.

### Appliance

This page displays appliance health status and network interfaces in the **Appliance Health Status Table** and **Appliance Network Interface Table**, high availability nodes in the **HA Node Table**, and license information in the **License Table**.
