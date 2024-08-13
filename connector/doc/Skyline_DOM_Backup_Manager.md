---
uid: Connector_help_Skyline_DOM_Backup_Manager
---

# Skyline DOM Backup Manager

This is a generic connector that ingest all of the available **DOM modules in the DMS** and takes a backup of each module based on user requirements.

## About
The **Skyline DOM Backup Manager** helps users that depends alot on **DOM** for their day to day operations to have a peace of mind that if something goes wrong with their system, that all the DOM modules will be backed up. This connector offers the ability to include DOM Instances in the backups along with some quality of life configuration for e.g. Frequency of backups, Maximum of Backups, etc. This connector paired with the **Skyline DOM Restore Manager** will give users the ultimate experience.

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Initial Version</li></ul>         |-         |-         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

There is no require initialization needed after creating the element. Everything else will be based on the user.

### Redundancy

There is no redundancy defined.

## How to use

### Backups Schdeule

The **Backups Schedule** page contains all the **avaiable DOM modules** in a table. In this table there are a few configuration parameters to help with the backup functionality of this connector.
- **Auotmatic Backups**: As the name suggest, this will take a backup automatically based on the **frequency define by the user**, if this is disabled no backups will be made.
- **Frequency**: The user can choose between **every hour**, **every 12 hours**, **every day**, **every week**, and **every month** for automatic backups.
- **Maximum Amount of Backups**: This will limit the amount of backups that are made to **prevent overloading the disk space**. Once the limit has been met, **the connector will delete the oldest backup file for the new backup file**.
- **Instances State**: This will include/exclude the **DOM instances** in the backup file.
- **Backup button**: the user can manually backup a particular DOM module.

On this page there are two configuration standalone parameters, 
- **Backup File Path** which allows the user to enter a path where the backup will be stored. **Default: C:\Skyline DataMiner\Documnets**
- **Sync Button** This allows the user to manually **update the table with all DOM modules in the DMS**.

### Configuration
On the **Configuration** page of this connector, the user can configure
- The **DMS Sync State** allows the **connector to sync the backup files across the DMS** if the **Backup File Path contains C:\Skyline DataMiner\Documents**
- The **DOM Module Sync Frequency** allow the user to set how often the connector will **check for DOM modules in the system**. **Minimum: 1 Hour Maximum: 24 Hours**

