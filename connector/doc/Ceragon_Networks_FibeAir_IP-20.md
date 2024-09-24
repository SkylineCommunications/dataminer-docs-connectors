---
uid: Connector_help_Ceragon_Networks_FibeAir_IP-20
---

# Ceragon Networks FibeAir IP-20

This connector retrieves information from a Ceragon Networks FibeAir IP-20 via SNMP.

Ceragon FiberAir IP-20G is a hybrid, split-mount hauling solution for edge and ring node. Supporting all common features of the IP-20 platform. FibeAir IP-20G boosts performance in today's networks while providing a cost-effective path to the furure network requirements. It offers full support for TDM services, as well as rich set of advanced carrier ethernet services providing a wide range of new capabilities that address the diverse and evolving needs of mobile backhaul, ISPs, utilities, government and private networks.

## About

The **FiberAir IP-20G** connector displays the general information, available interfaces, radio and ethernet configuration of the device. All information is retrieved using SNMP.

### Version Info

| Range   | Description      | Based on | System Impact |
|---------|------------------|----------|---------------------|
| 1.0.0.x | Initial version  | -        | -             |
| 1.0.1.x | - Displayed column layout for the Interfaces table changed because of added new rate parameters.<br>- Display key Interfaces table changed because previous format was not unique. Format now consists of "\[Description\].\[Index\] - \[Alias\]".<br>- Added bit rate in Ethernet Statistics table.<br>- Added rate parameters for Discarded, Broadcast, Unicast (in/out) packets.<br>- Added rate parameters for all counters available in Interface Physical Port RMON Statistics table. | 1.0.0.4  | - Verify applications, e.g. Reporter, that take the order of columns into account.<br> - Verify any configured alarm filter in the DMS to match the new format. |

### Product Info

| Range   | Supported Firmware Version |
|---------|----------------------------|
| 1.0.0.x | -                          |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components    | Exported Components    |
|-----------|---------------------|-------------------------|----------------------|------------------------|
| 1.0.0.x   | Yes                 | Yes                     | -                    | -                      |
| 1.0.1.x   | Yes                 | Yes                     | -                    | -                      |

## Installation and configuration

### Creation

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private.*

## Usage

### General

This page displays general information about the device, including the **System and Unit Information**, and all the information regarding the available interfaces that have been **enabled/disabled** in the system.

This page also has three subpages, which you can access through page buttons:

- The **Unit Inventory** subpage contains basic information about the unit that is currently installed, such as the device and part number, or the card name defined by vendor.
- The **NTP Configuration** subpage contains information regarding the **NTP Status** and **NTP Configuration**. You can check the poll interval, the lock state, and the IP of the sync server. The configuration table allows you to change the Admin state, NTP version, or even the server IP.

### Interfaces

This page displays information on the interfaces that are being used on a Ceragon device such as Ethernet, radio, and management ports. It is also possible to get information on the services that are running in the system, more specifically, TDM, LAG, or cascading options. All of them are configurable and you can activate or shut down ports.

### TDM/NGPW

On this page, you can activate or deactivate a set of 16 TDM(E1) ports.

This page also has three subpages, which you can access through page buttons:

- The **NGPW Services** subpage contains basic information of any NGPW. PSN Type, DS0 bundle configuration, slot, and pseudowire ID are some of the available features that can be seen/changed both for the services and PSN tunnels. The administrative status can also be configured.
- The **TDM PMs** subpage contains information regarding the errors on the transmission path. The counters can be divided into four different intervals: minutes, hours, current minute, or current hour.
- The **NGPW PMs** subpage contains an extended set of information regarding pseudowire error counters.

### Radio

This page shows both the status and configuration tables regarding the radio frequency unit.

This page also has four subpages, which you can access through page buttons:

- The **Remote Radio** subpage contains basic information about the remote radio connected to Ceragon FibeAir devices. Any remote radio parameter can be read or set on this subpage, such as the operational status, IP Address, RX and TX levels. As a workaround, you can also reset the radio here.
- The **Radio Threshold** subpage contains information regarding the possible threshold levels that allow the equipment to work correctly.
- The **Radio PMs** subpage contains an extended set of information regarding the throughput, average throughput, peak capacity or average capacity of the radio on a certain interval. Once again, the interval is between 15min, 15min current, 24 hour, 24hour current.
- The **MRMC PMs** subpage contains an extended set of counter information regarding the profile and bit rate of a radio for a specific interval. The interval can be 15 min, 15 min current, 24 hours, or 24 hours current.

### Ethernet

This page shows both the status and configuration tables regarding the physical Ethernet connections.

This page contains settings related to the media type used, the operational status, the negotiation of a connection, the speed and the quality of the connection agreement (half/full duplex).

In addition, it contains a subpage for the **Ethernet Services** provided, which can accessed through a page button. This subpage contains information regarding the Ethernet service type, administrative status, default CoS, EVC ID and description, and several other details regarding the trails, protection, encapsulatuib, and V-LAN.

### Cascading

This page contains settings related to the **Cascading configuration**. In this section, an Ethernet port (out of six ports) can be set as a cascading port. When this setting is changed, this will be reflected in the Interfaces table in the Interfaces tab.

### Virtual Tables

This page shows four tables in total. Two are mainly used for management purposes and the other two tables are used for booking resources allocation.

- **Radio Table**: Maximum bandwidth is the maximum bandwidth possible for the radio equipment. The available bandwidth is the total sum of current active and current booked bandwidth subtracted from the maximum bandwidth.

- **Ethernet Ports Table**: This table displays the Ethernet port status information. The status can be *Available*, *Used*, *Booked and Used*, *Booked*, and *Booked and available*. Another column shows the booked bandwidth allocated to each port.

- **E1 Virtual Interfaces Table**: This table displays all the 16 E1 "ports" that can be booked via an Automation script. In this table, each entry has the following information: Port Status, Reference, End Date, Booked Bandwidth, Contact, Metadata, and "Valid", which shows how much time still remains until the booking expires.

- **Ethernet Virtual Interfaces Table**: This table displays all 6 Ethernet ports that can be booked via an Automation script. This is similar to the E1 Virtual Interfaces table.

### Web Interface

This page displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
