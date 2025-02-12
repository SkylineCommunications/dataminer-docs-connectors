---
uid: Connector_help_Cisco_NSO
---

# Cisco NSO

The Cisco Network Services Orchestrator (NSO) is a orchestration platform for hybrid networks. It provides comprehensive lifecycle service automation to enable you to design and deliver high-quality services faster and more easily.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |5.7.X        |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination. (default: *443*)
  - **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.


### Initialization
After creating a new element it is necessary that the user specifies the login credentials in the General page

## How to use

In the **General** page the user can define the login credentials required for establishing communication with the device.

In the **Details** page the table Check IPTV details shows information for each IPTV Provider, like the Primary Site, the Primary Device, the Secondary Site and the Last Primary Site Chang timestamp. 

## Notes

This Cisco (NSO) implementation has been customized specifically for Bouygues Telecom. It incorporates proprietary API calls and integrations developed exclusively for Bouygues Telecom’s operational requirements. The configurations, workflows, and functionalities contained herein are tailored to meet the unique specifications of Bouygues Telecom and may not be applicable, transferable, or suitable for other use cases or organizations. Unauthorized use, replication, or distribution of this implementation is strictly prohibited.
For any inquiries or permissions, please contact the squad: squad.deploy-scrumbledore@skyline.be directly.
