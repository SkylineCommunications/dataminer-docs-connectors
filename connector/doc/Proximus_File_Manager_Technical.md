---
uid: Connector_help_Proximus_File_Manager_Technical
---

# Proximus File Manager

## About

This is a DataMiner connector custom to Proximus. The Proximus File Manager receives commands and their outputs from other elements via InterApp communication, thus allowing custom monitoring of commands. The connector processes each command output it receives and displays it either in a numeric table or a string table for monitoring and trending.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

## How to use

The **General** page shows the **Remote Commands Table**, which contains all of the received commands, the outputs, and the originating DataMiner element.

The **Numeric Values** page contains the **Numeric Table**, which shows all processed command outputs that contain a numeric value.

The **String Values** page contains the **String Table**, which displays processed command outputs that have a string value.

All three tables are equipped with a **context menu** that allows you to remove any command. Removing a command from the **Remote Commands Table** will also delete its entry from the **Numeric** or **String Table** if the command's output was successfully parsed. The same is true in reverse: removing a command from the **Numeric** or **String Table** will also remove it from the **Remote Commands Table**.

You can set a custom output description in the **Numeric** and **String Table**.

## Notes

If a command output fails to be processed, it will be listed in the **Remote Commands Table**, but not in the other tables.

Removed command outputs may be automatically re-added later, as this process depends on the remote element sending InterApp messages.
