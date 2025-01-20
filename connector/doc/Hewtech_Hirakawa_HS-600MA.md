---
uid: Connector_help_Hewtech_Hirakawa_HS-600MA
---

# Hewtech Hirakawa HS-600MA

This connector monitors information from the Hewtech Hirakawa HS-600MA, an industrial network switch with PTP support for precise time synchronization, PoE capabilities, and robust LLDP and VLAN support, ideal for high-reliability applications.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | v1_3_2                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### SSH Main Connection

This connector uses an SSH connection and requires the following input during element creation:

SSH CONNECTION:

- **IP address/host**: The polling IP of the device.
- **Port**: The SSH port of the device, by default **22**.

### Initialization

You must enter a valid **User Name** and **Password** to connect to the device. To do so, on the **SSH Settings** page, fill in the correct credentials.

### Save settings
For configured device settings to persist across device restarts, there is a need to save them. This is done via the **Save Config** button in the **General** page.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

- **General** page: Contains system information data, providing an overview of the current status and configuration of the device.
- **SSH Settings** page: Contains **User Name** and **Password** boxes where the credentials should be filled in for the SSH polling.
- **IP** page and subpages: Contains information about IP Interfaces, IP Routes, IP Routing Info, and IP Neighbor Info.
- **DNS** page: Contains settings related to DNS servers.
- **NTP** page: Contains settings related to NTP servers.
- **Log** page: Contains system log information with a warning or error level.
- **Interfaces Counters** page and subpages: Contains Size, Queuing, and Error RX and TX counters.
- **Ports** page: Contains switch port information.
- **IGMP Snooping** page: Contains IGMP snooping information and settings for multicast traffic optimization.
- **MLD Snooping** page: Contains MLD snooping information and settings similar to IGMP Snooping but for IPv6.
- **LLDP** page and subpages: Contains settings and information for LLDP Interface, LLDP-MED, LLDP Neighbors, and LLDP Port Statistics.
- **PoE** page: Contains PoE configuration.
- **VLAN** page: Contains Port VLAN configuration.
- **Private VLAN** page: Contains Private VLAN configuration.
- **PTP** pages: Contains Boundary clock and Transparent clock information and configuration.
