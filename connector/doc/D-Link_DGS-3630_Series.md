---
uid: Connector_help_D-Link_DGS-3630_Series
---

# D-Link DGS-3630 Series

The DGS-3630 Series is a range of Layer 3 Stackable Managed Switches. This connector can be used to monitor and configure such a device.

## About

The connector uses an **SNMP** connection.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 2.25.B025              |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMPv2 settings:

- **Port number**: The port of the connected device, e.g. *161.*
- **Get community string**: The community string used when reading values from the device, e.g. *public.*
- **Set community string**: The community string used when setting values on the device, e.g. *private*.

## Usage

### General

This page displays general information about the device, such as the **Name**, **Location**, and **Description**.

It also contains the following buttons:

- **ICMP**: Displays ICPM Stats and Message Stats.
- **System Services**: Displays a page listing the state of the services of each OSI layer.
- **TCP/UDP**: Displays a page with all TCP and UDP status parameters.
- **TCP Connection**: Displays a page with a list of TCP connections and TCP listeners.
- **UDP Endpoint**: Displays a page with a list of UDP endpoints.
- **Security**: Displays a page with the sercurity parameters, including the **Port security** tables.
- **Drive Info**: Displays a table with a list of the drive's information.

### SSH

This page contains the **SSH Configure Parameters**, which include SSH version, Timeout, and Authentication Retries. This Page also includes **SSH User** table which will display a list of the SSH user information.

### Power

This page contains parameters for configuring system power settings, including **Mini USB**, **LED** and **Power** table, 

The page also contains the following subpages:

- **LLDP EEE**: Display tables for configuring **LLDP Remote EEE** and **LLDP Local EEE**.

### Safegurad Engine

This page contains safegurad engine parameters inlduing **Safegurad Engine** configuration, **Fan** and **Air Flow** tables:

This page also contains the following sub-pages:

- **CPU**: Displays overall CPU statistics.
- **CPU Protect**: Display CPU protect rare limit configuration
- **Memory**: Displays information regarding the RAM.
- **Temperature**: Displays switch temperature information.

### PTP

The Precision Time Protocol (PTP) pages display information regarding this functionality.

This page contains the following subpages:

- **PTP Clock**: Displays parameters regarding the clock.
- **PTP Foreign Master**: Displays a table regarding the foreign master.
- **PTP Port**: Displays a table regarding the PTP port status.

### Unit

This page contains tables that display the Unit information of the switch, including the Unit status, and runtime.

### Alarm

This page contains a table that displays alarms in the switch.

### File Configuration

This page contains a table that displays file copy information and a table that contains information for replacing the current running configuration file.

### Boot Image

This page displays parameters that configure the boot image properties. This page also displays tables that show the current boot image URL and status.

### Time Clock

This page contains parameters that display and configure the switch clock.

### Source Interface IP

This page contains parameters that display and configure the different source interface IP addresses, including **TFTP**, **FTP**, and **RCP**. and **SSH**.

### Interface Detailed

This page contains the **Detailed Interface table**. This table provides general information about each interface.

### Interface Rx

This page contains the **Interface Rx table**. This contains the input statistics of each interface.

### Interface Tx

This page contains the **Interface Tx table**. This contains the output statistics of each interface.

### L2 Features

This page contains the **L2 Features** parameters, which are used to configure the L2 interface settings. Including MAC change, and Load Balance.

This page contains the following subpages:

- **L2 Interface Control**: Displays **L2 FDB interface** status and control parameters
- **L2 Channel Control**: Displays channel group properties
- **L2 Protocol**: Display parameters that control the L2 protocol interface, including tables for L2 protocol interface control.
- **L2 Global Control**: Displays parameters for the L2 interface global control.
- **L2 MAC**: Displays parameter for **L2 Tunneling MAC** control.

### L3 Features
This page displays the MPLS L3 VRF and configuration settings. 

This page contains the following subpages:

- **L3 VRF**: Displays a table which shows the L3 VPN VRF information and configuration parameters.
- **L3 VRF Route Targe**: Displays a table that specifies pre-VRF route target association.
- **L3 VRF Config**: Displays a table which contaons the L3 VPN interface configuration.

### ACL

This page displays the **Re-Sequencing table**. This table contains information about how to re-sequence the rules in the access lists.

This page contains the following subpages:

- **ACL IP**: Display tables for configuring the IP Access rule.
- **ACL IPv6**: Display tables for configuring IPv6 Access rule.
- **ACL MAC**: Display tables for configuring the MAC Access rule.

### Ethernet

This page contains the **Ethernet Stats table**, which displays information about ethernet stats for each ethernet interface.

### Storm Control

This page contains general configuration regarding storm control.

The page also contains the following subpages:

- **Storm Control Interface**: Displays a table containing all storm control interfaces and their action type.
- **Strom Control Thresholds**: Displays a table containing thresholds control for each of the storm control interfaces.
- **Strom Control Traffic Info**: Displays a table containing traffic info for each of the storm control interfaces.

### IP

This page displays general IP statistics and settings such as **Spin Lock**, **IP Forwarding**, and **IP Address Table**.

The page also contains the following subpages:

- **IPv4**: Displays a page containing the **IPv4 Interface table**.
- **IPv6**: Displays a page with the ***IPv6 Interface table** and **IPv6 Scope Zone Index Table**.
- **IP Route**: Displays a page containing the IP Route settings, including **IP Default Route Table**, **Ipv6 Route Table**, and **IPv6 Route Advert Spin Lock**.
- **Net to Physical**: Displays a page containing the **IP Net to Physical Table**, which is used for mapping from IP address to physical address. 

### Single Switch IP

This page provides general single switch IP information and configuration, including **IP Version**, **IP Capability**, and **IP Platform**.

The page also contains the following subpages:

- **IPMS**: Display a **Switch Single IPMS Table**, which contains information about the member switches that belong to the single IP management group.
- **Candidate Switches**: Display a **Switch Single IP Candidate Switches Table**
- **IP Group**: Displays tables for the Single IP Group information.
- **Zone Defense**: Displays tables for configuring Zone Defense Rules.

### POE Group

This page displays the POE group configuration and information for the POE group.

### POE Interface

This page displays tables for the POE interface configuration, including **POE Interface Config Table**, **POE Interface Status Table**, **POE Interface Measurement Table**, and **POE Interface PD Alive Config Table**.

### BGP

This page displays BGP general information and a table for the **BGP Global Setting**.

The page also contains the following subpages:

- **BGP Peers**: Display a **BGP Peer Table** and a **Switch BGP Peer Table** for BGP peer configurations.
- **BGP Peers AF**: Display a **BGP Peer AF Table** for BGP peer AF configuration.
- **BGP Peers Group**: Display tables for BGP groups information and configuration
- **BGP Route**: Display a **BGP Route Table**.
- **BGP Dampening Config**: Display parameters for BGP damping configuration.
- **BGP Network**: Display a table for BGP network addresses.
- **BGP Aggregate**: Display a table for BGP aggregate addresses.
- **BGP 4**: Display a **BGP 4 Path Attribute Table**.

### IMBP

This page displays **IMBP Global** Configuration parameter and a **IMPB Interface Config Table**

The page also contains the following subpages:

- **IMBP Violation**: Display parameters for IMBP Violation configuration and a table to display the **IMBP Violation Log**

### SNMP

This page displays general configuration parameters for switch SNMP. Including **SNMP Services**, **SNMP Local Engine ID**, and **SNMP Global Settings**.

The page also contains the following subpages:

- **Access Control**: Display tables that are used for config the SNMP access. Including **SNMP Community Table**, **SNMP Group Table**, **SNMP Host Table**, and **SNMP User Table**.
- **Context Mapping**: Display a **SNMP Context Mapping Table**.
- **SNMP Trap**: Display SNMP trapping setting parameters and a **SNMP Trap Interface Configuration Table**.

### OSPF

This page contains general information regarding the Open Shortest Path First protocol.

The page also contains the following subpages:

- **OSPF Area**: Displays a page containing the **OSPF Area** and **Stub Area table**. The Area table displays the configured parameters and cumulative statistics of the attached areas of the router. 
The Stub Area table contains the set of metrics that is advertised by a default Area Border Router in a stub area.
- **OSPF LSDB**: Displays the **LSDB table**, which displays information about the Link State Database of the OSPF process.
- **OSPF Host**: Displays a page containing the **Host table**, which displays the metrics of the hosts, which the router will advertise as host routes.
- **OSPF Interface**: Displays a page containing the **Interface**, **Interface Metric**, and **Virtual Interface tables**.
- **OSPF Neighbor**: Displays a page with the **OSPF Virtual Neighbor** and **OSPF Neighbor tables**.

### Physical Port Interface

This page contains tables regarding the physical port interface information and packet monitoring.

### Spanning Tree

This page displays parameters regarding the spanning tree global settings and **STP Extension Port** information.

### Stacking Topology

This page contains Stacking Topology general setting parameters, including **Box ID**, **Admin**, **Preempt**, etc.

### VLAN

This page contains tables and parameters for the general settings of the VLAN.

The page also contains the following subpages:

- **Port VLAN**: Display a **Port VLAN Interface Control Table**.
- **MAC VLAN**: Display tables for controlling MAC VLAN

### LLDP

This page displays LLDP general configuring parameters, including **LLDP Forward**, **LLDP Trap**, and **LLDP Clear Global Stats**, etc.

The page also contains the following subpages:

- **LLDP Port**: Display LLDP port configuration tables.
- **LLDP VLAN**: Display tables for configuring LLDP VLAN.

### SNTP

This page displays SNTP general config parameters and a **SNTP Server Table**.

### DHCP

This page displays **DHCP Relay Agent** config parameters as well as the **Relay Option 82** config parameters.

The page also contains the following subpages:

- **DHCP Relay**: Display parameters and table for DHCP Relay information.
- **DHCP Relay Option 82**: Display parameters and table for DHCP Relay Option 82 information.
- **Pool Relay**: Display DHCP Pool Relay tables, including **DHCP Pool Class Relay Target Table**, **DHCP Pool Relay Destination Table**, and **DHCP Pool Relay Source Table**.
- **DHCP Agent Interface**: Display tables for configuring DHCP Agent Interface. Including **DHCP Interface Info Policy Table**, and **DHCP Interface Agent Info Trust Table**.
- **DHCP Agent Control**: Display tables for configuring DHCP Agent Interface Control. Including **DHCP Interface Agent Info State Control**, and **DHCP Interface Agent Info Check Table**.
- **DHCP Agent Insert**: Display tables for configuring DHCP Agent Interface Insert. Including **DHCP Interface Agent Info Intert**, and **DHCP interface Agent Info Insert VPN Table**.