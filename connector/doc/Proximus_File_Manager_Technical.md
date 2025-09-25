---
uid: Connector_help_Proximus_File_Manager_Technical
---

# Proximus File Manager

## About

This is a DataMiner connector custom to Proximus. The Proximus File Manager receives via InterApp Communication commands and their outputs from other elements, thus allowing for custom monitoring of commands. Once received, the connector processes each command output and displays either on Numeric or String Table for monitoring and trending.

### Version Info

|Range              |Features           |Based on   |System Impact  |
|---------          |---------          |---------  |---------      |
|1.0.0.x [SLC Main] |Initial version    |-          |-              |

### System Info

In this subsection, insert a table with five columns. Indicate whether the range features **DCF integration** and whether it is **Cassandra compliant**.

In the "Linked Components"; column, list all DataMiner components that have a link, in any way, with this connector range, e.g. mediation connectors, Automation scripts, custom report, etc.

In the "Exported Components" column, list all the connectors that are exported by the parent connector in question.
**This can only be omitted for an exported connector or for a connector that cannot have exported connectors.**

|Range      |DCF Integration    |Cassandra Compliant    |Linked Components  |Exported Components|
|---------  |---------          |---------              |---------          |---------          |
|1.0.0.x    |No                 |Yes                    |-                  |                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to use

The **General** page shows the **Remote Commands Table** which contains all of the received commands, outputs, and the originating DataMiner element.

The **Numeric Values** page contains the **Numeric Table**, which shows all processed command outputs that contain a numeric value.

The **String Values** page contains the **String Table**, which displays processed command outputs that have a string value.

All three tables are equipped with a **Context Menu** which allows the user to remove any command. Removing from the **Remote Commands Table** will also delete its entry from the **Numeric** or **String Table** if the command's output was successfully parsed The same is true in reverse, removing a command from the **Numeric** or **String Table** will also remove it from the **Remote Commands Table**.

The user can set a custom output description on **Numeric** and **String Table**.

## Notes

If a command output fails to be processed, it will be listed in the **Remote Commands Table** but not on **Numeric** or **String Table**.

Removed command outputs may be automatically re-added later, as this process depends on the remote element sending InterApp messages.
