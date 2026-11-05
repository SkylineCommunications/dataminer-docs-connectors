---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_Channel_Management_Technical
description: "Configure and use the Vodafone Kabel Deutschland GmbH Channel Management connector to view and refresh channel and service DOM data in DataMiner."
---

# Vodafone Kabel Deutschland GmbH Channel Management

## About

The Vodafone Kabel Deutschland GmbH Channel Management connector retrieves and displays channel and service data from a DataMiner Object Models (DOM) database. If the database does not yet exist, the connector creates it.

## Configuration

### Connections

No connections need to be configured for this connector during element creation.

### Automation Scripts

To use this connector, make sure the following automation scripts are installed on the DataMiner Agent:

- *InitializeVodafoneChannelManagementDomDatabase*
- *RefreshVodafoneChannelManagementDomTables*

## How to Use

Once the element has been created, the **Channels** and **Services** tables will be automatically refreshed with the most recent data.

While this data is periodically refreshed, you can also force a refresh with the **Refresh [Table Name] Table** button, which is located above each table.
