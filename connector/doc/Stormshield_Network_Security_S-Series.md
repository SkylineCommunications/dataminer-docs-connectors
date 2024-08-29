---
uid: Connector_help_Stormshield_Network_Security_S-Series
---

# Stormshield Network Security S-Series

## About
This connector is used to collect SNMP data from any **Stormshield Network Security S-Series** equipment.
The **Stormshield Network Security S-Series** is a range of next-generation firewalls offering advanced threat protection, unified security features, and high performance. It supports scalable deployment, secure VPN connections, and centralized management. Designed for organizations of all sizes, it helps ensure robust network security without compromising performance.
### Version Info
This
| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [SLC Main]| Initial version | - | - |


### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   |    4.3.25    |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SNMP Connection - Main
This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:
SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization

No extra configuration is needed.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use 

The connector contains the following data pages:

- **General**: Contains generic information data like **Model**, **Version**, **Serial Number**. Also some **Memory Usage** and **Number of Interfaces** parameters can be found.

- **Health**: Contains the **Health Table**, with some relevant system status information, **Power Supplies Table** with the status for all Power Supplies of the device, **CPU Table** that provides the temperatures of all CPUs available, and the **Auto Update Table** that as as entries all the available Sub-Systems and their Update date and status.

- **Alarms**: Contains the **Alarms Table**.

- **IPSEC**: Contains the IP Security Parameters like number of **Security Policies** and **Associations**.

- **VPN**: Contains the VPN **Security Association**, **Internet Key Exchange Security Association** and **Security Policy** tables.

- **Hosts**: Contains the **Hosts Table** where we can find Throughput and Packets informations for each Host.

- **Interfaces**: Contains the **Interfaces Table**  where we can find Throughput for the different connections/protocols for each interface.

- **Services**: Contains the **Services Table** with the Service State and UpTime.

- **Policies**: Contains the **Policies Table** with Policy **Name** and respective **Slot Index**.

- **ASQ Stats**: Contains the **Automated Speed Quality Statistics** parameters organized by Network Protocol Type.

- **Routes**: Contains the **Routes Table** with the infrmation relative to each **Route**.

- **QOS Stats**: Contains the **Quality of Service Statistics Table** with **Traffic** and **Speed** information. 

- **Polling Configuration**: On this page, you can select which of the available requests is polled and when. You can also poll the requests on demand with the **Refresh** button for each entry in the table. With the **Refresh All** button, you can poll all requests on demand at once.
