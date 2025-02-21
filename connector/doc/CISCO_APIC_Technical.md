---
uid: Connector_help_CISCO_APIC_Technical
---

# CISCO APIC

## About

The CISCO APIC (Application Policy Infrastructure Controller) is a software-based solution that is a core component of Cisco's Application Centric Infrastructure (ACI). It serves as the centralized management and automation point for the ACI fabric, providing a single point of control for policy definition and network automation.

With this connector, you can monitor CISCO devices monitored by the CISCO APIC.

## Configuration

### Connections

#### SNMP Connection

This connector uses an SNMPv2 connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: The community string used when setting values on the device, by default *private*.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use (1.0.0.x)

The element created with this connector consists of the following data pages:

- **General**: Displays general **system information** as well as the **System OR** table, which lists the capabilities of the local SNMP applications acting as a command responder with respect to various MIB modules.

- **Physical Entities**: Displays information about the physical entities monitored by the CISCO APIC. The components of a physical entity are interpreted as physical entities themselves, so the device hierarchy of a physical entity is shown within the display key column, making sure the physical entity's source is clearly represented.

  The subpages of this page display physical entities that are sensors. You can enable alarm monitoring and trending on the status and value reported by the sensor in order to pinpoint issues with the physical entity.

- **CPU**: Displays the **CPUs** table.

  Note that the polled SNMP index is not saved over reboots for the CISCO APIC. Because of this limitation in the software, alarm and trend info will be removed when a reboot on the CISCO APIC is detected. This is done to prevent a mismatch in trending and alarming.

- **Power**: Displays power related physical entities.

- **Web Interface**: Displays the web interface of the polling IP address.
