---
uid: Connector_help_Sony_MLS-X1
---

# Sony MLS-X1

The Modular Live System (MLS-X1) is a production switcher platform.
It is reconfigurable to meet a wide range of live production requirements, it provides processing power and scalability to enhance your production environments.

The MLS-X1 inherits the operability, reliability and capability of Sony other professional switchers.
It uses multiple smaller processing units that can be rapidly configured according to the requirements of any production.
With the MLS-X1 you’ve got the power to cater for large-scale events – including multi-programme and multi-format productions – plus the agility to meet future demands.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>System monitoring through SNMP</li><li>System configuration through gRPC</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |-        |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |Yes       |Yes         |-         |   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]
- **IP port**: [The IP port of the destination. (default: *161*)]


SNMP Settings:

- **Get community string**: [The community string used when reading values from the device. (default: *public*)]
- **Set community string**: [The community string used when setting values on the device. (default: *private*)]


### Initialization

This connector also uses gRPC (Google Remote Procedure Call) to manage and configure the system.
It will use up to 5 gRPC connections to gather information and to configure the different systems.

#### Manager gRPC Connection

In the **MLS Manager** page, you will need to configure the following parameters:

Manager gRPC Connection:

- **IP address/Hostname**: [The IP of the destination. (default: *Polling Ip*)]
- **IP port**: [The IP port of the destination. (default: *31042*)]
- **Username**: [The login username.]
- **Password**: [The login password.]

#### Logical Switcher gRPC Connection

In the **Logical Switcher** page, you will need to configure the following parameters (the IP address is the one obtained in the *System Configurations* table in the **MLS Manager** page):

Logical Switcher gRPC Connection:

- **IP port**: [The IP port of the destination. (default: *9181*)]
- **Username**: [The login username.]
- **Password**: [The login password.]

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

- **General**: This page contains general information, such as the **System Description**, **System Up Time**, **System Contact**, **Name**, and **Location**. It also displays an overview of the **OSI Model** of the availability of each layer, as well as the Agent and Switcher **MIB Versions**.
- **Network**: This page displays the **Interfaces** and **Address Translation** tables. The Interfaces table displays the operational status of the interfaces available in the workstation. This operational status can also change based on incoming traps.
- **Product Information**: This page displays the **Product Information**, **Modules**, and **Remote Maintenance** tables.
- **Traps**: This page displays the **Traps Destination** table.
- **Alarms**: This page displays the **Error Status** table. This table is cleared when a "Coldstart" trap is received.
- **XVS Control**: This page allows you to check which XVS element is connected to which the XVS via the **Control Interfaces** table. There is a **Resubscribe** button to reset all the created subscriptions.
- **Subscriptions**: This page allows you to check all the created subscriptions by this element.
- **Agent MIB**: This page displays the **Agent MIB Categories** and **Agent MIB Products** tables.
- **Switcher Information**: This page displays the **Switcher Reference Information**, **Switcher Temperature Information**, **Switcher Fan Information**, **Switcher Power Sensors**, **Switcher SSD Information**, and **Switcher Battery Information** tables.
- **MLS Manager**: This page displays the **MLS Manager** gRPC connection credentials and state, as well as some system configurations.
- **Logical Switcher**: This page displays the **Logical Switcher** gRPC connections. It also displays some information about each connection and connected device.

## Dataminer Connectivity Framework

The **1.0.0.x** range of the Sony MLS-X1 connector supports the usage of DCF.

**DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (e.g. a manager).**


### Interfaces

#### Dynamic interfaces

- The Interfaces table is available with type **inout**.