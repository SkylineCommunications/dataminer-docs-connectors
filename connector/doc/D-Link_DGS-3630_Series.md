---
uid: Connector_help_D-Link_DGS-3630_Series
---

# D-Link DGS-3630 Series

The DGS-3630 Series is a range of Layer-3 Stackable Managed Switches. This connector can be used to monitor and configure such devices.

The connector uses an **SNMP** connection.

## About

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
- **Get community string**: The community string used when reading values from the device, e.g. *public*.
- **Set community string**: The community string used when setting values on the device, e.g. *private*.

## Usage

### General

This page displays general information about the device, such as the **Name**, **Location**, and **Description**.

It also contains the following buttons:

- **ICMP**: Displays ICMP and message statistics.
- **System Services**: Displays a page listing the state of the services of each OSI layer.
- **TCP/UDP**: Displays a page with all TCP and UDP status parameters.
- **TCP Connection**: Displays a page with a list of TCP connections and TCP listeners.
- **UDP Endpoint**: Displays a page with a list of UDP endpoints.
- **Security**: Displays a page with the security parameters, including the **Port security** tables.
- **Drive Info**: Displays a table with the drive's information.

### SSH

This page contains the **SSH configuration parameters**, which include SSH Version, Timeout, and Authentication Retries.

This page also includes the **SSH User** table, which displays a list of the SSH user information.

### Power

This page contains parameters for configuring system power settings, including **Mini USB** and the **LED** and **Power** table.

The page also contains a page button to the **LLDP EEE** subpage, which displays tables for configuring **LLDP Remote EEE** and **LLDP Local EEE**.

### Safeguard Engine

This page contains safeguard engine parameters including the **Safeguard Engine** configuration, and the **Fan** and **Air Flow** tables.

This page has the following subpages:

- **CPU**: Displays overall CPU statistics.
- **CPU Protect**: Displays the CPU protect rare limit configuration.
- **Memory**: Displays information regarding RAM.
- **Temperature**: Displays switch temperature information.

### PTP

This page displays information regarding the Precision Time Protocol (PTP) functionality.

This page has the following subpages:

- **PTP Clock**: Displays parameters regarding the clock.
- **PTP Foreign Master**: Displays a table regarding the foreign master.
- **PTP Port**: Displays a table with PTP port status information.

### Unit

This page contains tables that display unit information for the switch, including the unit status and runtime.

### Alarm

This page contains a table that displays the alarms in the switch.

### File Configuration

This page contains a table that displays file copy information, as well as a table that contains information for replacing the current running configuration file.

### Boot Image

On this page, you can configure the boot image properties. The page also displays tables that show the current boot image URL and status.

### Time Clock

On this page, you can view and configure parameters related to the switch clock.

### Source Interface IP

On this page, you can view and configure parameters related to the different source interface IP addresses, including **TFTP**, **FTP**, and **RCP**. and **SSH**.

### Interface Detailed

This page contains the **Detailed Interface table**. This table provides general information about each interface.

### Interface Rx

This page contains the **Interface Rx table**. This contains the input statistics of each interface.

### Interface Tx

This page contains the **Interface Tx table**. This contains the output statistics of each interface.

### L2 Features

This page contains the **L2 Features** parameters, which are used to configure the L2 interface settings. This includes the MAC change and load balance.

This page has the following subpages:

- **L2 Interface Control**: Displays **L2 FDB interface** status and control parameters
- **L2 Channel Control**: Displays channel group properties
- **L2 Protocol**: Displays parameters and tables that control the L2 protocol interface.
- **L2 Global Control**: Displays parameters for the L2 interface global control.
- **L2 MAC**: Displays the **L2 Tunneling MAC** control.

### L3 Features

This page displays the MPLS L3 VRF and configuration settings.

This page contains the following subpages:

- **L3 VRF**: Displays a table with the L3 VPN VRF information and configuration parameters.
- **L3 VRF Route Targe**: Displays a table that specifies the pre-VRF route target association.
- **L3 VRF Config**: Displays a table with the L3 VPN interface configuration.

### ACL

This page displays the **Re-Sequencing table**. This table contains information about how to re-sequence the rules in the access lists.

This page has the following subpages:

- **ACL IP**: Displays tables for configuring the IP access rule.
- **ACL IPv6**: Displays tables for configuring IPv6 access rule.
- **ACL MAC**: Displays tables for configuring the MAC access rule.

### Ethernet

This page contains the **Ethernet Stats table**, which displays information about Ethernet stats for each Ethernet interface.

### Storm Control

This page contains the general configuration regarding storm control.

The page also has the following subpages:

- **Storm Control Interface**: Displays a table listing all storm control interfaces and their action type.
- **Storm Control Thresholds**: Displays a table with the thresholds control for each of the storm control interfaces.
- **Storm Control Traffic Info**: Displays a table containing traffic info for each of the storm control interfaces.

### IP

This page displays general IP statistics and settings such as **Spin Lock**, **IP Forwarding**, and **IP Address Table**.

The page also has the following subpages:

- **IPv4**: Displays a page containing the **IPv4 Interface table**.
- **IPv6**: Displays a page with the **IPv6 Interface table** and **IPv6 Scope Zone Index Table**.
- **IP Route**: Displays a page containing the IP route settings, including **IP Default Route Table**, **Ipv6 Route Table**, and **IPv6 Route Advert Spin Lock**.
- **Net to Physical**: Displays a page containing the **IP Net to Physical Table**, which is used for mapping from IP address to physical address.

### Single Switch IP

This page provides general single switch IP information and configuration, including **IP Version**, **IP Capability**, and **IP Platform**.

The page also has the following subpages:

- **IPMS**: Displays the **Switch Single IPMS Table**, which contains information about the member switches that belong to the single IP management group.
- **Candidate Switches**: Displays the **Switch Single IP Candidate Switches Table**.
- **IP Group**: Displays tables with single IP group information.
- **Zone Defense**: Displays tables for the configuration of zone defense rules.

### POE Group

This page displays the POE group configuration and information for the POE group.

### POE Interface

This page displays tables for the POE interface configuration, including **POE Interface Config Table**, **POE Interface Status Table**, **POE Interface Measurement Table**, and **POE Interface PD Alive Config Table**.

### BGP

This page displays BGP general information and a table for the **BGP Global Setting**.

The page also has the following subpages:

- **BGP Peers**: Displays the **BGP Peer Table** and the **Switch BGP Peer Table** for BGP peer configuration.
- **BGP Peers AF**: Displays the **BGP Peer AF Table** for BGP peer AF configuration.
- **BGP Peers Group**: Displays tables for BGP groups information and configuration.
- **BGP Route**: Displays the **BGP Route Table**.
- **BGP Dampening Config**: Displays parameters for the BGP damping configuration.
- **BGP Network**: Displays a table with BGP network addresses.
- **BGP Aggregate**: Displays a table with BGP aggregate addresses.
- **BGP 4**: Displays the **BGP 4 Path Attribute Table**.

### IMBP

This page displays the **IMBP Global** configuration parameter and the **IMBP Interface Config Table**.

The **IMBP Violation** page button displays parameters for the IMBP violation configuration and a table with the **IMBP Violation Log**.

### SNMP

This page displays general configuration parameters for switch SNMP, including **SNMP Services**, **SNMP Local Engine ID**, and **SNMP Global Settings**.

The page also contains the following subpages:

- **Access Control**: Displays tables that are used for the configuration of SNMP access, including **SNMP Community Table**, **SNMP Group Table**, **SNMP Host Table**, and **SNMP User Table**.
- **Context Mapping**: Displays the **SNMP Context Mapping Table**.
- **SNMP Trap**: Displays SNMP trap settings and the **SNMP Trap Interface Configuration Table**.

### OSPF

This page contains general information regarding the Open Shortest Path First (OSPF) protocol.

The page also contains the following subpages:

- **OSPF Area**: Displays a page containing the **OSPF Area** and **Stub Area table**. The Area table displays the configured parameters and cumulative statistics of the attached areas of the router. The Stub Area table contains the set of metrics that is advertised by a default Area Border Router in a stub area.
- **OSPF LSDB**: Displays the **LSDB table**, which displays information about the Link State Database of the OSPF process.
- **OSPF Host**: Displays a page containing the **Host table**, which displays the metrics of the hosts, which the router will advertise as host routes.
- **OSPF Interface**: Displays a page containing the **Interface**, **Interface Metric**, and **Virtual Interface tables**.
- **OSPF Neighbor**: Displays a page with the **OSPF Virtual Neighbor** and **OSPF Neighbor tables**.

### Physical Port Interface

This page contains tables regarding the physical port interface information and packet monitoring.

### Spanning Tree

This page displays the spanning tree global settings and **STP Extension Port** information.

### Stacking Topology

This page contains general settings related to stacking topology, including **Box ID**, **Admin**, **Preempt**, etc.

### VLAN

This page contains tables and parameters for the general settings of the VLAN.

The page also contains the following subpages:

- **Port VLAN**: Displays a **Port VLAN Interface Control Table**.
- **MAC VLAN**: Displays tables for the MAC VLAN configuration.

### LLDP

This page displays general LLDP configuration parameters, including **LLDP Forward**, **LLDP Trap**, and **LLDP Clear Global Stats**, etc.

The page also contains the following subpages:

- **LLDP Port**: Displays LLDP port configuration tables.
- **LLDP VLAN**: Displays tables for the LLDP VLAN configuration.

### SNTP

This page displays SNTP general configuration parameters and the **SNTP Server Table**.

### DHCP

This page displays **DHCP Relay Agent** configuration parameters as well as the **Relay Option 82** configuration parameters.

The page also contains the following subpages:

- **DHCP Relay**: Displays parameters and a table with DHCP relay information.
- **DHCP Relay Option 82**: Displays parameters and a table with DHCP Relay Option 82 information.
- **Pool Relay**: Displays DHCP Pool Relay tables, including the **DHCP Pool Class Relay Target Table**, **DHCP Pool Relay Destination Table**, and **DHCP Pool Relay Source Table**.
- **DHCP Agent Interface**: Displays tables for configuring the DHCP Agent Interface, including the **DHCP Interface Info Policy Table** and **DHCP Interface Agent Info Trust Table**.
- **DHCP Agent Control**: Displays tables for configuring the DHCP Agent Interface Control, including the **DHCP Interface Agent Info State Control** and **DHCP Interface Agent Info Check Table**.
- **DHCP Agent Insert**: Displays tables for configuring the DHCP Agent Interface Insert, including the **DHCP Interface Agent Info Insert** and **DHCP interface Agent Info Insert VPN Table**.
