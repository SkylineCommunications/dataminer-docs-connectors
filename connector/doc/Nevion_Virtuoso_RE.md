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

Element using this connector will display both manager and card data, polling of manager data is always enabled and requests are being sent on a timer basis. 
Polling of the card data needs to be configured on the **Slots** table, **Slots** page, where polling for any card can be enabled/disabled and a polling frequency for each card can be configured separately.

The element using this connector consists of the data pages detailed below.

- General: Contains general information data and a subpage Authentication where user name and password can be configured.
- Slots: Contains table **Slots** which displays card data and allows for polling configuration of each card. Table **Modules** contains all available modules and their data.
- Cards: Contains tables for card data, such as **Product Information**, **Time Information**, **Memory Information** and **Memory Thresholds**.
- Alarm Profiles: Contains Alarm Profiles (Alarm Definitions) information.
- Alarms: Contains active alarms information.
- Temperature: Contains all the data related to the temperature, including tables for temperature zones, sensors and fans.
- Memory: Contains memory data, and additional custom table parameter **Threshold Reached** which displays if used / free memory ratio is above a defined percentage threshold.
- Power: Contains all the data related to the power, including table for power sensors.
- Sessions: Contains tables **Users**, which shows users and their level, and **Sessions**, which show currently connected users, their level and session duration.
- Files: Contains data about files and **Configuration** table.
- Inputs: Contains inputs data, displayed in **TS-IP Inputs** table.
- Switch: Contains switch data, displayed in **TS Input Switch** and **TS Switch Inputs** tables.
- Outputs: Contains outputs data, displayed in **TS-IP Outputs** table.
- SNTP: Contains SNTP information.
- Ethernet: Contains **Ethernet**, **Ethernet Status**, **LLDP Remote** and **Reference Sync Input** tables as well as two subpages: Routing (**Rx Routing** and **Tx Routing**) and Rates (**Rx Rates** and **Tx Rates**).
- SFP: Contains data related to SFP, displayed in **SFP** and **SFP Channels** tables.
- Network Config: Contains **DNS** table as well as two subpages: Services (with **Services** table) and Static IP Routing (with tables for **IPv4** and **IPv6**).
- Interfaces: Contains interfaces data, displayed in **Interfaces** table.
