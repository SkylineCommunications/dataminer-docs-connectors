---
uid: Connector_help_Vodafone_Kabel_Deutschland_GmbH_SI_Stream_Mapping
---

# Vodafone Kabel Deutschland GmbH SI Stream Mapping

This is a dedicated connector intended to store the links between the DataMiner Reservations, Input information and outgoing SDT/EIT PID information.
The saved data tables within the connector are required by the SRM (Service and Resource Management) framework to setup the SI Streams correctly for the IP Gateway, IP Peering and SRT Gateway use cases.

## About

### Version Info

| **Range**            | **Key Features**    | **Based on** | **System Impact** |
|----------------------|---------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version     | -            | -                 |

### Product Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Redundancy

There is no redundancy defined.

## How to use

The **IP GW**, **IP Peering** and **SRT** pages display the linked configurations between DataMiner reservations and SDT/EIT information.  
You can perform several actions on this table via its right-click menu.
