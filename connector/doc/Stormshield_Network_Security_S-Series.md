---
uid: Connector_help_Stormshield_Network_Security_S-Series
---

# Stormshield Network Security S-Series

This connector is used to collect SNMP data from any **Stormshield Network Security S-Series** equipment.

The **Stormshield Network Security S-Series** is a range of next-generation firewalls offering advanced threat protection, unified security features, and high performance. It supports scalable deployment, secure VPN connections, and centralized management.

## About

### Version Info

| Range              | Key Features    | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 4.3.25             |

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

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The connector has the following data pages:

- **General**: Displays general information like the **Model**, **Version**, and **Serial Number**, as well as the **Memory Usage** and **Number of Interfaces**.

- **Health**: Contains the **Health Table**, with some relevant system status information, the **Power Supplies Table**, with status information for all power supplies of the device, the **CPU Table**, which shows the temperatures of all available CPUs, and the **Auto Update Table**, which lists the available subsystems and their update date and status.

- **Alarms**: Contains the **Alarms Table**.

- **IPSEC**: Displays IP security parameters such as the number of **Security Policies** and **Associations**.

- **VPN**: Contains the VPN **Security Association**, **Internet Key Exchange Security Association**, and **Security Policy** tables.

- **Hosts**: Contains the **Hosts Table**, where you can find the throughput and packets information for each host.

- **Interfaces**: Contains the **Interfaces Table**, which shows the throughput for the different connections/protocols for each interface.

- **Services**: Contains the **Services Table**, with the service state and uptime.

- **Policies**: Contains the **Policies Table**, with the policy name and respective slot index.

- **ASQ Stats**: Contains the **Automated Speed Quality Statistics** parameters organized by network protocol type.

- **Routes**: Contains the **Routes Table**, with information related to each route.

- **QOS Stats**: Contains the **Quality of Service Statistics Table**, with traffic and speed information.

- **Polling Configuration**: On this page, you can select which of the available requests is polled and when. You can also poll the requests on demand with the **Refresh** button for each entry in the table. With the **Refresh All** button, you can poll all requests on demand at once.
