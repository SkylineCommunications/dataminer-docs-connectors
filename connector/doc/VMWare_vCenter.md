---
uid: Connector_help_VMWare_vCenter
---

# VMWare vCenter

## About

VMware vCenter Server provides a centralized platform for managing your VMware vSphere environments, allowing you to automate and deliver a virtual infrastructure across the hybrid cloud with confidence.

The VMWare vCenter connector enables DataMiner to communicate with a VMWare vCenter Server, allowing a user to remotely monitor and operate a vCenter server.

### Version Info

| Range     | Description                                                                 | DCF Integration     | Cassandra Compliant     |
|------------------|------------------------------------------------------------------------------|---------------------|-------------------------|
| 1.0.0.x          | Initial version                                                              | No                  | Yes                    |
| 1.0.1.x          | Improve performance when polling big amounts of data (multi-threaded timers). | No                  | Yes                    |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | API Version 6.5             |
| 1.0.1.x          | API Version 6.5             |

## Installation and configuration

### Creation

#### HTTP Main Connection

This connector uses a HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device. Default: *443*.

### Initialization

When you have created the element, go to the **Polling Configurations** page, fill in the **Username** and **Password** fields, and then click the **Authenticate** button. If the authentication is successful, the connector will start polling data. (See [Polling Configurations](#polling-configurations).)

## How to Use

### General

On this page, a variety of general data is displayed. The available data features mostly system- and product-related data and a variety of subpages such as:

- **Advanced Networking**
- **Health**
- **Networking**
- **Partitions**
- **Security**
- **Services**
- **SNMP Settings**

This page and all subpages are populated using the **Appliance API**.

### Polling Configurations

On this page, you can set up the login credentials so that the connector can communicate successfully with the VMWare vCenter Server. (See [Initialization](#initialization))

If the login is successful, the REST vCenter API Status, REST Appliance API Status, and the Web Service API Status will eventually be successful.

A **toggle button** is available that allows you to **enable each API**. You will need to enable each API for which you want polling to occur. Currently, the connector supports the **vCenter API** (Data centers, Clusters, Hosts, Virtual Machines, Datastores, and Networks), **Appliance API** (General Data), and the **Web Services API** (Performance Data).

Refer to the connector log if the login is unsuccessful.

### Datacenter Topology

This page displays the data center topology as well as its assigned clusters, hosts, and virtual machines.

A variety of data is provided in this topology.

Performance information for hosts and virtual machines is also shown.

### Hosts

This page displays all the hosts present in the VMWare vCenter Server.

### Virtual Machines

This page displays all the virtual machines configured in the VMWare vCenter Server.

### Storage

This page displays all the available storage, allowing you to check the storage capacity and the free capacity of the system.

### Networks

This page displays all the configured networks in the VMWare vCenter Server.

### Hosts Sensor Info

This page displays numeric sensor information for the hosts.

### Web Interface

This page displays the web interface of the device.

Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
