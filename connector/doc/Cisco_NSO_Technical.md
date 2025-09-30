---
uid: Connector_help_Cisco_NSO_Technical
---

# Cisco NSO

## About

The Cisco Network Services Orchestrator (NSO) is an orchestration platform for hybrid networks. It provides comprehensive life cycle service automation to enable you to design and deliver high-quality services faster and more easily.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination. (default: *443*)
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

When you have created the element, go to the **General** page and specify the login credentials so the connector can communicate with the Cisco NSO.

## How to use

On the **General** page, the login credentials should be specified to establish communication with the device.

On the **Details** page, the Check IPTV details table shows information for each IPTV provider, such as the Primary Site, the Primary Device, the Secondary Site, and the Last Primary Site Change timestamp.

## Notes

This is a user-specific Cisco (NSO) implementation. It incorporates proprietary API calls and integrations developed exclusively for this user. The configurations, workflows, and functionalities contained in this connector are tailored to meet unique specifications and may not be applicable, transferable, or suitable for other use cases or organizations. Unauthorized use, replication, or distribution of this implementation is strictly prohibited.

For any inquiries or permissions, please contact <squad.deploy-scrumbledore@skyline.be>.
