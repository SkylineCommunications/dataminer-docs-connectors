---
uid: Connector_help_Infoblox_NIOS_Platform
---

# Infoblox NIOS Platform

The Network Identity Operating System (NIOS) is the operating system that powers Infoblox core network services, to ensure the operation of network infrastructures. The NIOS platform automates the deployment and management of network services such as DNS, DHCP, and IP address management (IPAM).

The Infoblox NIOS Platform connector enables the retrieval of important key performance indicators (KPIs) from the NIOS Platform via its API. These KPIs provide insights into the health and status of the deployed network infrastructure, including metrics such as  power supply levels, memory usage, and the status of services.

## About

### Version Info

| Range              | Features                                                      | Based on | System Impact |
|--------------------|---------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | - Network, member, and node monitoring.<br>- License validity | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 9.0.3-50212        |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

#### SNMP Connection

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

The Infoblox NIOS Platform connector uses both SNMP and HTTP connections to gather data. The SNMP connection retrieves basic information about the platform, including the hardware version, serial number, and NIOS version.

The HTTP connection provides access to important KPIs related to networks, members, and nodes, such as high-availability status and utilization metrics.

The connector also allows users to verify the license validity for the platform.

### Single Range Switching

In the **Network Ranges** table, you can switch a specific range to a different member. This is done through the **Member Name** column, which shows the currently active member for each range. Clicking on a member's name will open a dropdown listing all available members. Simply select a new member from the list to complete the switch.

### Bulk Range Switching

You can switch multiple ranges in bulk via the **Switch** subpage within the **Network Ranges** page.

On this subpage, select an **Active Member** and a **Switch Member** from their respective dropdown lists, which display all available members.

Once you click the **Switch** button, all ranges currently assigned to the selected **Active Member** will be reassigned to the specified **Switch Member**.

### Default Switching

You can reset all ranges to their default member, as listed in the **IBX DHCP Member** column of the **Network Ranges** table. To do this, navigate to the **Switch** subpage within the **Network Ranges** page and click the Switch Default button.