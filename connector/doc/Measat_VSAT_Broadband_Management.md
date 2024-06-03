---
uid: Connector_help_Measat_VSAT_Broadband_Management
---

# Measat VSAT Broadband Management

This a custom connector for Measat that retrieves data from an NMS and makes it available to be ingested by Measat's low-code app and dashboard. Custom parameters in the connector include the overall site count of the networks in East and West Malaysia and the congestion status of the group QOS.

At present, the following NMS is supported: iDirect.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 4.3.1.1            |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### MySQL Connection

This connector connects to a MySQL database and an archive database where data from the NMS is stored.

### Initialization

To set up the MySQL connection, configure the following parameters on the General page of the element:

- **Database Server**: The IP address of the MySQL server.
- **Database User Name**: The user name of the account to log into the MySQL server.
- **Database Password**: The password of the account to log into the MySQL server.
- **Database Name**: The name of the database being accessed on the MySQL server.

The Site Count archive database queries the state_change_log table to update the net modem statuses.

The Congestion archive database queries the nms_group_qos_changes table to update the Group QOS and congestion data.

## How to use

On the **General** page of this connector, you can configure the connection with the config and archive databases.

On the **Site Counts** page of this connector, you can view the networks in the West Malaysia and East Malaysia tables and the online and offline sites for each network. The overall site count is also present here for both the West Malaysia and East Malaysia gateways.

On the **Site Count Configuration** subpage, you can set the allowable sites for all of the networks in either West or East Malaysia at once and also set the alarm threshold for the status of the networks.

On the **Networks** subpage, you can view the net modems and networks that are present, as well as the current statuses.

On the **Congestion** page of this connector, you can view the Group QOS congestion status for both West and East Malaysia. The congestion is based on the upstream and downstream free bandwidth and the percentage of free bandwidth remaining.

On the **Congestion Configuration** subpage, you can set the threshold for when a group QOS would be considered congested.

On the **Group QOS** subpage, you can view the polled group QOS, including the Mesh Bandwidth and Multicast QOS.

### Notes

This connector is part of the VSAT Broadband Manager package, which also comes with low-code apps, dashboards, and Automation scripts.
