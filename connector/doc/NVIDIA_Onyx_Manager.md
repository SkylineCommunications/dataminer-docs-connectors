---
uid: Connector_help_NVIDIA_Onyx_Manager
---

# NVIDIA Onyx Manager

This connector is used to monitor the **Onyx Equipment** running on **NVIDIA**.

The information on tables and parameters is retrieved via SNMP polling and HTTP REST API.

## About

### Version Info

| Range              | Description            | Based on | System Impact |
|--------------------|------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version        | -        | -             |

### Product Info

| Range   | Supported Firmware                     |
|---------|----------------------------------------|
| 1.0.0.x | Software X86_64 3.10.4408 API 3.6.5000 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

During element creation, you will need to specify the IP addresses for both the SNMP and the HTTP connection.

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device, by default *80*.

### Initialization

On the [General - HTTP Connection](#general---http-connection) page, fill in the credentials so that the HTTP-related parameters can be polled.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## Usage

### General

This page displays the **System Name, System Description, System Location, System Contact, System Up Time**, and other general parameters.

### General - HTTP Connection

This page displays the configuration parameters for the HTTP connection. A successful login must be performed in order to poll the HTTP-related parameters.

- **Username**: The user account used to log in to the device.
- **Password**: The password associated with the user account.

### Detailed Interface Info

This page displays the **Detailed Interface Info** table.

### Interface Data

This page displays the **Ethernet Interface Data**, which contains extra information for the Ethernet interfaces.

### Detailed Interface Info - RX

This page displays the **Detailed Interface Info - Rx** table.

### Detailed Interface Info - TX

This page displays the **Interface Info - Tx** table.

### Chassis

This page displays information related to the chassis status of the device.

Via page buttons, information is also available on the **Fans**, **Modules**, **Clusters**, **CPU**, **Storage**, **STP**, and **Temperature**.

### PTP

This page displays the **PTP information**.

### Management Interface

This page displays the **Management Interface** table, which contains the information for the management and loopback interfaces of the device.

### Transceiver Diagnostics

This page displays the **Transceiver Diagnostics** table. The table displays the diagnostic information related to the transceiver that attached to the specific port.

### IP Routing Info

This page displays the **IP Routing and ARP** tables.

### VLAN Info

This page displays the list of the existing VLANs currently configured on the device.

### Physical Entities

This page displays the **Physical Entities** device information in a table.

### DHCP

This page displays the DHCP relay instances information for both IPv4 and IPv6.

### IGMP

This page displays the list of the existing VLANs that have IGMP-enabled options.

### VRRP

This page displays the **VRRP (Virtual Router Redundancy Protocol) Information** table.

### VRF

This page displays the **VRF (Virtual Routing and Forwarding)** table.

### BGP

This page displays the **BGP (Border Gateway Protocol)** related tables. You can delete the BGP Summary or BGP Neighbor using the Delete button in the Action column.

### Dump Files

This page is used to create and download the **Dump File** from the device.

To create the dump file, click the **Create Dump File** button.

> [!IMPORTANT]
> The connector will time out during the creation of the dump file because the device will be busy and unable to process other requests. The process of creating the dump file will take approximately 5 minutes.

To download the dump file:

1. Fill in all configuration parameters on the **Download Configuration** page.
1. Use the **Download** button from the **Dump Files** table.

You can only download one file at a time.

### Web Interface

This page displays the web interface of the device. However, note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
