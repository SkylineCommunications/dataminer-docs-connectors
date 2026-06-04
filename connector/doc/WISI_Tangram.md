---
uid: Connector_help_WISI_Tangram
---

# WISI Tangram

The **WISI Tangram** connector is used to display and configure information of the attached modules as well as the main board. The WISI TANGRAM video platform is a high-density digital TV headend for contribution of digital TV via IP networks and end-to-end IPTV solutions such as video on demand, connected TV and OTT (Over The Top) or Web TV.

## About

The WISI Tangram connector works using SNMP commands and is also configured to receive traps. In addition, a UDP connection needs to be set up in order to receive syslog messages.

More information is provided on the following website: <http://wisi.de/en/business/products/tangram/>

This connector will export different connectors based on the retrieved data. A list can be found in the section "Exported Connectors".

## Key Features

- **Chassis and module monitoring**: Provides centralized visibility of chassis status, power supply, fan measurements, and a full module overview for all installed GT-series cards.
- **Dynamic Virtual Elements (DVEs)**: Automatically generates a dedicated DVE for each supported module type (GT21, GT22, GT23, GT31, GT34, GT41), enabling granular, per-module monitoring and configuration.
- **SNMP and syslog integration**: Combines SNMP polling and trap reception with syslog message ingestion over UDP, giving a comprehensive view of device events and failures.
- **Switch and VLAN management**: Exposes switch settings including VLAN configuration, multicast flooding control, IGMP snooping, and per-port bit rate statistics for the embedded GT11 switch.

## Use Case

**Challenge**: A broadcast operator runs a high-density digital TV headend using a WISI Tangram chassis populated with multiple GT-series processing modules. Monitoring and configuring each module individually through the native web interface is time-consuming, and there is no unified view of chassis health, module status, and network events.

**Solution**: The WISI Tangram connector integrates the entire chassis into DataMiner via SNMP and syslog. A main element provides chassis-level visibility, while DVEs are automatically created for each supported module, allowing operators to monitor and configure each card from a single DataMiner environment.

**Benefit**: Operators gain a consolidated view of all modules, switch settings, and system logs, enabling faster fault detection, streamlined configuration management, and reduced operational overhead across the digital TV headend.



## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_WISI_Tangram_Technical).
