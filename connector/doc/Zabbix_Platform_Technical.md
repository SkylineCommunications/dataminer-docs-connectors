---
uid: Connector_help_Zabbix_Platform_Technical
---

# Zabbix Platform

Zabbix is software that monitors numerous parameters of a network as well as the health and integrity of servers.

This HTTP connector connects to the Zabbix API to retrieve data from the Zabbix platform. The Zabbix API is a web-based API that is shipped as part of the web front end. It uses the JSON-RPC 2.0 protocol. This connector will export different connectors based on the retrieved hosts from the API. For more information on the device, refer to [Zabbix's documentation](https://www.zabbix.com/documentation/3.0/manual/api).

## About

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

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

To be able to retrieve data from the API, specify a **Username** and **Password** on the **Configuration** page.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General
The General page presents a tree view that allows you to drill down from a **Host Group** to an individual Host, and then inspect not only the host properties but also its **Triggers** and **Items**.

### Hosts
This page presents Zabbix's **Host Group** and **Host** information in two tables, along with **tag** filtering options, allowing users to quickly refine the list of hosts by applying tag-based filtering.

The **Host Group** table shows a list of host groups, identifying the group ID and Name. In this table users can also enable/disable the polling each each host group. 

The **Host** table shows the hosts belonging to the enabled groups, providing the operator with a consolidated view of all relevant host metadata. For each host, the table displays the host ID, name, status and group. Other properties such as Proxy Host, IPMI and Maintenance fields are also present.


Finally, this page also includes a button that opens the **Configure DVEs** subpage, allowing users to enable or disable DVE instantiation per host.

### Triggers
This page provides a comprehensive view of active triggers within the monitored environment. 
The table lists all triggers, each represented by its Trigger Id, Trigger Description, associated Host, Priority, and Value. 

### Items
The Item Table lists the monitoring items configured for the monitoring hosts. Each row represents an item with the name assigned to the check, and its description, which explains what the item monitors. The table also shows the last collected value and the timestamp of when it was last updated.

### Events
In the Events page, the table lists all events for the monitored hosts, displaying the related host and scope. Each row represents a specific event created (e.g., generated via trigger). The table displays the Event ID, the source, the object and its ID, and the timestamp of when the issue occurred. 

The properties indicating the current state (e.g., OK, Problem), if the event has been acknowledged, and its severity are also present in the Events table. 

### Correlations
The Correlations table lists correlation rules which allow Zabbix to compare multiple events and apply logic, such as closing related problems, suppressing noise, or linking events across hosts or services. 
The table includes columns for the Correlation ID, status, name of the rule, its description, the filter conditions.

### Problems
In the problems page users can define for how many days ago they want to poll the records. The Problems table will then list all currently active or historical problems. Each entry represents a specific problem state detected by Zabbix, displaying details such as the Event ID, a description of the trigger, the host where the issue occurred, and the timestamp when the problem was generated. The table also includes the source and object. 

### Configuration
The Configuration page displays the **API version** and allows you to define the **username**, **password**, and API **URL** required for connecting to the Zabbix Platform and retrieving data through the API.
