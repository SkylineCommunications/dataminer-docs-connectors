---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_Descrambling_Service
---

# Vodafone Kabel Deutschland GmbH Descrambling Service

The Vodafone Deutschland Descrambling service protocol monitors the outgoing streaming states per site included in the service.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | No | Yes | [Vodafone Kabel Deutschland GmbH Active Service Configuration Platform](xref:Connector_help_Vodafone_Kabel_Deutschland_GmbH_Active_Service_Configuration_Platform) | - |

## Configuration

### Connections

This is a service protocol. To create a service using this protocol:

1. In DataMiner Cube, right-click a view in the Surveyor and select *Create service*.
1. Specify the name for the service.
1. Open the advanced options and select the service protocol, *Vodafone Kabel Deutschland GmbH SAT DL Service*, with the latest version or production version.
1. Go to the *parameters* tab and include the service you want to monitor.

## How to use

The **General** page contains an overview of the active stream states per site.

The **Alarms** page contains a toggle button to retrieve and display all active alarms for the included services and elements.

The **Elements** page contains a toggle button to enable any debug logging related to the elements or retrieval of the data.

## Notes

This enhanced service protocol was designed for a specific project and is not expected to be reused in general.
