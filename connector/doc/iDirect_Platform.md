---
uid: Connector_help_iDirect_Platform
---

# iDirect Platform

## About

The iDirect Evolution NMS is a centralized interface for managing satellite communication networks. It provides real-time visibility into network health, remote terminal status, carrier configurations, and system performance.  

iDirect Platform connector provides the key data from iDirect Evolution NMS. The connector organizes data into logical sections for easy navigation and operational control of the complete NMS in a single element.  

## General

The General section displays all details about VSAT remotes and their operational state. It includes information such as platform ID, username, customer, modem role, current state, uptime, serial number, management IP address, and many more metrics. This section helps operators quickly assess the health and connectivity of remote terminals.

![General](~/connector/images/iDirect_Platform_General.png)

## Remote Platforms

The Remotes section provides detailed information about remote terminals and their associated inroute groups. It includes metrics such as the number of remotes per group, burst traffic, actual capacity, available bandwidth, and utilization. Additional tables show MODCOD compositions and symbol rate distributions for each inroute group.

![Inroute Group Statistics](~/connector/images/iDirect_Platform_Network_InrouteGroups.png)

![DVB-S2 Inroute Group Details](~/connector/images/iDirect_Platform_Network_DVB-S2_InrouteGroups.png)

![Inroute Group MODCOD Composition](~/connector/images/iDirect_Platform_Inroute_Group_Composition_Table.png)

## Network Summary

The Networks section summarizes active networks and their bandwidth usage. It includes downstream and upstream rates, teleport IDs, and booked bandwidth. Quality of Service (QoS) groups are also shown, detailing bandwidth allocation, utilization, and priority levels. MODCOD distribution tables provide insight into the modulation and coding schemes used across the network.

![Active Network Summary](~/connector/images/iDirect_Platform_Active_Networks.png)

![QoS Group Bandwidth Allocation](~/connector/images/iDirect_Platform_Network_Qos_Groups.png)

![MODCOD Distribution](~/connector/images/iDirect_Platform_Network_MODCOD.png)

## Linecard Status

The Linecards section shows the health and operational parameters of linecards installed in the chassis. It includes linecard type, status, temperature, transmit power, and error counts. Carrier frequency assignments and modulation settings are also displayed. Chassis-level views provide a summary of slot assignments and overall system health.

![Linecard Operational Metrics](~/connector/images/iDirect_Platform_Linecard.png)

![Linecard Carrier Frequency](~/connector/images/iDirect_Platform_Linecard_Carriers.png)

![Carrier Modulation](~/connector/images/iDirect_Platform_Carriers.png)

![Chassis Health Overview](~/connector/images/iDirect_Platform_Chassis.png)

![Chassis Slot/Linecard Mapping](~/connector/images/iDirect_Platform_Chassis_Tree.png)

## Polling Configuration

The Polling Configuration section displays the polling and Dynamic Virtual Element (DVE) state for each linecard. It includes whether polling is enabled, the DVE state, and the last active timestamp. This helps ensure that linecards are actively monitored and validated for performance.

![Polling/DVE Configuration Linecards](~/connector/images/iDirect_Platform_Linecard_DVE_Config.png)
