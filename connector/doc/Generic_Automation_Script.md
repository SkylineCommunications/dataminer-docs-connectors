---
uid: Connector_help_Generic_Automation_Script
---

# Generic automation Script

This connector can be used to launch automation scripts and get status information for those automation scripts.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version. | -            | -                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

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
