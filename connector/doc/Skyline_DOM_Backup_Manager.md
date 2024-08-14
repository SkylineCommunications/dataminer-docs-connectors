---
uid: Connector_help_Skyline_DOM_Backup_Manager
---

# Skyline DOM Backup Manager

This is a generic connector that ingests all of the available **DOM modules in the DMS** and takes a backup of each module based on user requirements.

It is intended for users that depend a lot on DOM for their day-to-day operations, so they can have the peace of mind of knowing that if something goes wrong with their system, all their DOM modules will be backed up.

This connector offers the ability to include DOM instances in the backups along with some quality-of-life configuration for e.g. frequency of backups, maximum backups, etc.

We recommend using this connector along with the **Skyline DOM Restore Manager** connector.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to use

### Backups Schedule Page

The **Backups Schedule** page lists all the **available DOM modules** in a table. The table also contains a number of configuration parameters to help with the backup functionality of this connector:

- **Automatic Backups**: This will take a backup automatically based on the frequency you define. If this is disabled, no backups will be created.
- **Frequency**: You can choose between **every hour**, **every 12 hours**, **every day**, **every week**, and **every month** for automatic backups.
- **Maximum Amount of Backups**: This will limit the number of backups that are made, to prevent taking up too much disk space. Once the limit is reached, the connector will **delete the oldest backup file** for the new backup file.
- **Instances State**: This will include or exclude the **DOM instances** in the backup file.
- **Backup button**: With this button, you can manually back up a particular DOM module.

There are also two standalone configuration parameters on this page:

- **Backup File Path**: The path where the backup will be stored. Default: `C:\Skyline DataMiner\Documents`.
- **Sync button**: This allows you to manually **update the table** with all DOM modules in the DMS.

### Configuration Page

On the **Configuration** page of this connector, you can configure the following parameters:

- **DMS Sync State**: Allows the connector to sync the backup files across the DMS if the **Backup File Path** contains `C:\Skyline DataMiner\Documents`.
- **DOM Module Sync Frequency**: Determines how often the connector will check for DOM modules in the system. **Minimum**: 1 Hour. **Maximum**: 24 Hours.
