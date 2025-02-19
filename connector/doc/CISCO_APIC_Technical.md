---
uid: Connector_help_CISCO_APIC_Technical
---

# CISCO APIC

The CISCO APIC (Application Policy Infrastructure Controller) is a software-based solution that is a core component of Cisco’s Application Centric Infrastructure (ACI).
It serves as the centralized management and automation point for the ACI fabric, providing a single point of control for policy definition and network automation.

With this driver, you can monitor CISCO devices monitored by the CISCO APIC.

## About

### Version Info

| Range              | Key Features                                                                                      | Based on | System Impact |
|--------------------|---------------------------------------------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version.                                                                                  | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | 5.3(2b)                |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses an SNMPv2 connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: [The polling IP or URL of the destination.]

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use (1.0.0.x)

The element created with this connector consists of the following data pages:

- **General**: Displays general **system information** as well as the **System OR** table, which lists the capabilities of the local SNMP applications acting as a command responder with respect to various MIB modules.
- **Physical Entities**: Displays information about the physical entities monitored by the CISCO APIC. The components of a physical entity are interpreted as physical entities themselves.
Therefore, the device hierarchy of a physical entity is shown within the display key column so that a physical entity's source is clearly represented.

	The subpages display physical entities that are sensors. The status and value reported by the sensor can be alarmed and trended on in order to pinpoint the issue with the physical entity.

- **CPU**: Displays the **CPUs** table. Do note that the polled snmp index is not saved over reboots for the CISCO APIC.
Due to the software's limitation, alarm and trend info will be wiped when a reboot on the CISCO APIC is detected.
This is done to prevent mismatch in trending and alarming.
-  **Power**: Displays power related physical entities.
- **Web Interface**: Displays the web interface of the polling IP address.