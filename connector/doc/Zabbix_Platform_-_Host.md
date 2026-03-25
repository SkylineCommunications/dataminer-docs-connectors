---
uid: Connector_help_Zabbix_Platform_-_Host
---

# Zabbix Platform - Host

Zabbix is software that monitors numerous parameters of a network as well as the health and integrity of servers.

## About

This is an **HTTP** connector that connects to the Zabbix API to retrieve data from the Zabbix platform. The Zabbix API is a web-based API and is shipped as part of the web front end. It uses the JSON-RPC 2.0 protocol. This connector is created by the **Zabbix platform** connector. For more information on the device, refer to [Zabbix's documentation](https://www.zabbix.com/documentation/current/en/manual/api).

### Version Info

| Range                | Key Features                            | Based on     | System Impact     |
|----------------------|-----------------------------------------|--------------|-------------------|
| 1.0.0.x [Obsolete]   | Initial version.                        | -            | -                 |
| 1.1.0.x [Obsolete]   | API 4.0: new features were implemented. | -            | -                 |
| 1.2.0.x [Obsolete]   | API 6.0: added support.                 | -            | -                 |
| 1.3.0.x [SLC Main]   | API 7.0: added support.                 | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |
| 1.1.0.x   | 4.0                    |
| 1.2.0.x   | 6.0                    |
| 1.3.0.x   | 7.0                    |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components                                                        |
|-----------|---------------------|-------------------------|-----------------------|----------------------------------------------------------------------------|
| 1.0.0.x   | No                  | Yes                     |                       |                                                                            |
| 1.1.0.x   | No                  | Yes                     | -                     | [Zabbix Platform - Host](xref:Connector_help_Zabbix_Platform_-_Host)       |
| 1.2.0.x   | No                  | Yes                     | -                     | [Zabbix Platform - Host](xref:Connector_help_Zabbix_Platform_-_Host)       |
| 1.3.0.x   | No                  | Yes                     | -                     | [Zabbix Platform - Host](xref:Connector_help_Zabbix_Platform_-_Host)       |

## Installation and configuration

### Creation

The element using this protocol is **automatically created** by the parent connector (Zabbix platform). The name of the element consists of the name of the parent connector + host.

### Configuration

To be able to retrieve data from the API, the **Username, Password** and **URL** must be provided on the Configuration page of the parent element.

## Usage

### General

This page displays information about the host, providing the operator with a consolidated view of all relevant host metadata. The page displays the host name, status and group. Other properties such as Proxy Host, IPMI and Maintenance fields are also present.

### Triggers
The table lists all triggers for the monitored host, each represented by its Trigger Id, Trigger Description, and Priority.

### Problems
The Problems table lists all currently active or historical problems for the specific host. Each entry represents a specific problem state detected by Zabbix, displaying details such as the Event ID, a description of the trigger, the host where the issue occurred, and the timestamp when the problem was generated. The table also includes the source and object.

### Items
The Item Table lists the monitoring items configured for the specific host. Each row represents an item with the name assigned to the check, and its description, which explains what the item monitors. The table also shows the last collected value and the timestamp of when it was last updated.

