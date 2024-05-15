---
uid: Connector_help_Mellanox_Technologies_MLNX-OS_Manager
---

# Mellanox Technologies MLNX-OS Manager

This connector is used to monitor the **Mellanox Equipment** running on **MLNX-OS**.

The information on tables and parameters is retrieved via SNMP polling. Specific range versions provide additional information in accordance with the API device documentation.

## About

### Version Info

| Range              | Description            | Based on | System Impact |
|--------------------|------------------------|----------|---------------|
| 1.0.0.x            | Initial version        | -        | -             |
| 1.1.0.x [SLC Main] | HTTP connection added. | 1.0.0.1  | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |
| 1.1.0.x | API 3.6.5000       |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |
| 1.1.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

#### HTTP Connection (added in range 1.1.0.x)

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device.
- **IP port**: The IP port of the device, by default *80*.

## Usage (all ranges except 1.1.0.x)

### General

This page displays the following general information: **System Name**, **System Description**, **System Location**, **System Contact**, **System Up Time** and other general parameters.

On this page, you can also enable the polling of tables.

### Detailed Interface Info

This page displays the **Detailed Interface Info** table. In this table, the columns **Tx/Rx Bitrate daily, weekly and monthly** display the amount of data.

The **Rx/Tx errors rate** can be retrieved within a defined **interval of time**.

All counters can be reset using the **Reset All Counters** button and this can be rolled back with the **Undo** button.

### Detailed Interface Info - Rx

This page displays the **Detailed Interface Info - Rx** table.

### Detailed Interface Info - Tx

This page displays the **Detailed Interface Info - Tx** table.

### IP Routing Info

This page displays the **IP Routing and ARP** tables.

## Usage (1.1.0.x only)

### General

This page displays the following general information: **System Name, System Description, System Location, System Contact, System Up Time** and other general parameters.

On this page, you can also enable the polling of tables.

### Detailed Interface Info

This page displays the **Detailed Interface Info** table. In this table, the columns **Tx/Rx Bitrate daily, weekly and monthly** contain the amount of data.

The **Rx/Tx errors rate** can be retrieved within a defined **interval of time**.

The **Interface Counter Telemetry Connection State** displays the current status of the **Interface Counter** telemetry session. The status will display **Connected** if the connector is currently listening to the telemetry session.

### Telemetry Settings

This page displays parameters used for the configuration of the telemetry settings to subscribe to the Mellanox **Interface Counter telemetry sessions**:

- The **TCP Listener IP Address** and **Data Source Port** indicate the IP address and port to create the TCP network client for listening to device telemetry data.

- The **Interface Polling Mode** is used to switch the polling mode between **SNMP** and **Telemetry** for the Detailed Interface Info table, Detailed Interface Info - RX table, and Detailed Interface Info - TX table.

- The **Interface Detail Debug** parameter allows you to enable debugging mode for telemetry. When this is enabled, the connector will log incoming telemetry data in the element's logging.

To start listening or subscribing to the Interface Counter telemetry session:

1. Configure the client IP address and port on the Mellanox device.

1. Configure the TCP Listener IP and Data Source Port parameters in the element.

   The values of both parameters must be the same as what is configured in the Mellanox device.

1. Switch the interface polling mode to *Telemetry*.

### Detailed Interface Info - RX

This page displays the **Detailed Interface Info - Rx** table.

### Detailed Interface Info - TX

This page displays the **Interface Info - Tx** table.

### Chassis

This page displays information related to the chassis status of the device. This includes **Spanning Tree Protocol**, **OSPF**, **Routing** and **LACP**.

Via page buttons, information is also available on the **Fans**, **Modules**, **Clusters** and **Temperature**.

### Management Interface

This page displays the **Management Interface** device information in a table.

### IP Routing Info

This page displays the **IP Routing and ARP** tables.

### Physical Entities

This page displays the **Physical Entities** device information in a table.

### VLAN Info

This page displays the list of the existing VLANs currently configured on the device.

### IGMP

This page displays the list of the existing VLANs that have IGMP-enabled options.

### VRF

This page displays the **VRF (Virtual Routing and Forwarding)** table.

### PTP

This page displays the **PTP information**.

### Explorer

This page allows you to send commands to the device.

### Web Interface

This page displays the web interface of the device. However, note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
