---
uid: Connector_help_Sony_MLS-X1
---

# Sony MLS-X1

The Modular Live System (MLS-X1) is a production switcher platform. It can be configured to meet a wide range of live production requirements, and it provides processing power and scalability to enhance production environments.

The MLS-X1 inherits the operability, reliability, and capability of other Sony professional switchers. It uses multiple smaller processing units that can be rapidly configured according to the requirements of any production. This allows you to cater for large-scale events, including multi-program and multi-format productions, and it provides the agility to meet future demands.

## About

### Version Info

| Range              | Features                                                                | Based on | System Impact |
|--------------------|-------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | - System monitoring through SNMP<br>- System configuration through gRPC | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | -                  |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | Yes             | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

This connector also uses gRPC (Google Remote Procedure Call) to manage and configure the system. It will use up to 5 gRPC connections to gather information and to configure the different systems, which will need to be configured in the element.

#### Manager gRPC Connection

On the **MLS Manager** page, configure the following parameters for the Manager gRPC connection:

- **IP address/Hostname**: The IP of the destination (default: *Polling IP*).
- **IP port**: The IP port of the destination (default: *31042*).
- **Username**: The login username.
- **Password**: The login password.

#### Logical Switcher gRPC Connection

On the **Logical Switcher** page, configure the following parameters:

Logical Switcher gRPC Connection:

- **IP port**: The IP port of the destination (default: *9181*). You can obtain this from the **System Configurations** table on the **MLS Manager** page.
- **Username**: The login username.
- **Password**: The login password.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

- **General**: This page contains general information, such as the **System Description**, **System Up Time**, **System Contact**, **Name**, and **Location**. It also displays an overview of the **OSI Model** of the availability of each layer, as well as the Agent and Switcher **MIB Versions**.
- **Network**: This page displays the **Interfaces** and **Address Translation** tables. The Interfaces table displays the operational status of the interfaces available in the workstation. This operational status can also change based on incoming traps.
- **Product Information**: This page displays the **Product Information**, **Modules**, and **Remote Maintenance** tables.
- **Traps**: This page displays the **Traps Destination** table.
- **Alarms**: This page displays the **Error Status** table. This table is cleared when a "Coldstart" trap is received.
- **XVS Control**: This page allows you to check which XVS element is connected to which XVS via the **Control Interfaces** table. There is a **Resubscribe** button to reset all the created subscriptions.
- **Subscriptions**: This page allows you to check all the subscriptions created by this element.
- **Agent MIB**: This page displays the **Agent MIB Categories** and **Agent MIB Products** tables.
- **Switcher Information**: This page displays the **Switcher Reference Information**, **Switcher Temperature Information**, **Switcher Fan Information**, **Switcher Power Sensors**, **Switcher SSD Information**, and **Switcher Battery Information** tables.
- **MLS Manager**: This page displays the **MLS Manager** gRPC connection credentials and state, as well as some system settings.
- **Logical Switcher**: This page displays the **Logical Switcher** gRPC connections. It also displays some information about each connection and connected device.

## DataMiner Connectivity Framework

The **1.0.0.x** range of the Sony MLS-X1 connector supports the usage of DCF.

DCF can also be implemented through the DataMiner DCF user interface and through third-party DataMiner connectors (e.g. a manager).

### Interfaces

#### Dynamic interfaces

- In the Interfaces table, dynamic interfaces are available with type **inout**.
