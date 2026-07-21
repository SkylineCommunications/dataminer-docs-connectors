---
uid: Connector_help_Generic_Automation_Script
---

# Generic Automation Script

## About

This connector can be used to launch automation scripts and get status information for those automation scripts.

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## How to use

This connector allows you to launch automation scripts and check information on those automation scripts.

To use the connector, set the parameter **Request** with a block of JSON code to start the script, for example:
*{"ScriptName": "ExtractMaterials","ScriptParams": {"ContentXml": "Test"},"ScriptDummies":{"FunctionDve":{"DmaId":123,"ElementId":456}}}*

## Notes

The DLL **ProcessAutomation.dll** must be available in the system.
