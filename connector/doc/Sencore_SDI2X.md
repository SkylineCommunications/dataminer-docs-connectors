---
uid: Connector_help_Sencore_SDI2X
---

# Sencore SDI2X
The Sencore SDI2X connector is used to monitor **Sencore SDI2X** device.

The device supports both SDI to IP and IP to SDI workflows. It also supports SMPTE 2022-6 and TR-03/SMPTE 2110.

The user can configure the direction (SDI->IP or IP->SDI) for each channel independently.

The platform supports one or more channels which can be configured to convert SDI video inputs into IP output streams, or IP input streams into SDI video outputs. 
The platform will encapsulate or de-encapsulate the SDI video according to SMPTE 2022-6 standard.
The platform also supports redundancy using SMPTE 2022-7 seamless switching standard.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [SLC Main] | Initial version. | - | - |

### Product Info

| Range     | Supported Firmware         |
|-----------|----------------------------|
| 1.0.0.x   |1.2.3|

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--|--|--|--|--|
| 1.0.0.x | No | Yes | - ||

## Configuration

### Connections

#### SNMP Main Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: Default:*161*.

SNMP Settings:

- **Get community string**: Default: *public-community.*
- **Set community string**: Default: *private-community.*

### Initialization

No extra configuration is needed.

### Redundancy

There is no redundancy defined.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use
The connector contains **General**, **Channels**, **Input**, **Output** and **Alarms** data pages.

On **General** page you can find generic status and informations parameters .

Below **General** page there are **Network**, **Date/Time**, **SNMP** and **Syslog** sub-pages that contain status and configuration parameters.

On the **Channels** page you can find every configuration related to each different channel along with their Inputs and Outputs.

On the **Input** page there are available other Input related configuration parameters that are not related with **Channel**.

On the **Outputs** page you can find the same as **Inputs** page.

At least on the **Alarms** page you can find the **Alarms** and **Events Log** tables.
