---
uid: Connector_help_Nevion_Virtuoso_RE
---

# Nevion Virtuoso RE

This is a DataMiner connector for the Nevion Virtuoso RE, a media server designed for broadcast carrier-class applications. The connector uses an HTTP connection to allow monitoring of the Nevion Virtuoso RE.

## About

### Version Info

| Range              | Key Features                                        | Based on | System Impact |
|--------------------|-----------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. Includes all available monitoring. | -        | -             |

### Product Info

| Range     | Supported Firmware |
|-----------|--------------------|
| 1.0.0.x   | 1.0.8              |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination (fixed value: 80).
  - **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify BypassProxy.

### Initialization

To make sure the connector can retrieve data, fill in the **User Name** and **Password** of the device on the **Authentication** subpage of the **General** page.

## How to use

Elements using this connector will display both manager and card data.

Polling of manager data is always enabled, and requests are sent based on a timer.

Polling of the card data needs to be configured in the **Slots** table (on the Slots page). There you can enable or disable the polling for any card, and you can configure the polling frequency for each card separately.

The element using this connector consists of the following data pages:

- **General**: Contains general information data. On the **Authentication** subpage, the username and password to connect with the device need to be configured.
- **Slots**: Contains the **Slots** table, which displays card data and allows you to configure the polling for each card. The **Modules** table contains all available modules and their data.
- **Cards**: Contains tables for card data, such as **Product Information**, **Time Information**, **Memory Information**, and **Memory Thresholds**.
- **Alarm Profiles**: Contains information related to alarm profiles (alarm definitions).
- **Alarms**: Contains information related to active alarms.
- **Temperature**: Contains all the data related to the temperature, including tables for temperature zones, sensors, and fans.
- **Memory**: Contains memory data. In addition, the custom table parameter **Threshold Reached** displays if the used/free memory ratio is above a defined percentage threshold.
- **Power**: Contains all the data related to the power, including a table for the power sensors.
- **Sessions**: Contains the **Users** table, which shows users and their level, and the **Sessions**, which show the currently connected users, their level, and the session duration.
- **Files**: Contains data about files, as well as the **Configuration** table.
- **Inputs**: Contains inputs data, displayed in the **TS-IP Inputs** table.
- **Switch**: Contains switch data, displayed in the **TS Input Switch** and **TS Switch Inputs** tables.
- **Outputs**: Contains outputs data, displayed in the **TS-IP Outputs** table.
- **SNTP**: Contains SNTP information.
- **Ethernet**: Contains the **Ethernet**, **Ethernet Status**, **LLDP Remote**, and **Reference Sync Input** tables, as well as two subpages: **Routing** (Rx Routing and Tx Routing) and **Rates** (Rx Rates and Tx Rates).
- **SFP**: Contains data related to SFP, displayed in the **SFP** and **SFP Channels** tables.
- **Network Config**: Contains the **DNS** table as well as two subpages: **Services** (with the Services table) and **Static IP Routing** (with tables for IPv4 and IPv6).
- **Interfaces**: Contains interfaces data, displayed in the **Interfaces** table.
