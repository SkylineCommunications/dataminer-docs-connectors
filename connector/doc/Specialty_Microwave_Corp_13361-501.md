---
uid: Connector_help_Specialty_Microwave_Corp_13361-501
---

# Specialty Microwave Corp 13361-501

This is a DataMiner connector for the ADSS uplink switching control panel. The equipment consist of a logic panel used in satellite communication earth stations.

## About

### Version Info

| Range              | Features         | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 0222          |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### Serial Connection - Main

This connector uses a serial connection and requires the following input during element creation:

SERIAL CONNECTION:
- Interface connection:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination.
  - **Bus Address**: The bus address of the destination. (default: *1*, range: ASCII values ! to ~ )

## How to use

On the **General** page of this connector, you can configure the position of a switch by selecting the position in the dropdown menu of the switch parameter.
