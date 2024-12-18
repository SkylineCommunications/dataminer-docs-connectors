---
uid: Connector_help_2WCOM_MPX-2ds
---

# 2WCOM MPX-2ds

The MPX-2ds is a two-channel decoder designed for MPX distribution via satellite or IP.

The 2WCOM MPX-2ds connector's main purpose is to monitor the two channels of the decoder.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | 1.24               |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | -                 | -                   |

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *161*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

## Featured Pages

  - **General**: Includes information on the status of the device, including some general information.
    
  - **Services**: The available Services will be displayed in this page, as entries of the table **ServicesInfo**, each representing a decoder channel. Information about each decoder channel will be displayed here.
    
    - **Virtual Tables**: Virtual tables are displayed here, which will offer information that is used to build the **ServicesInfo** table found in the Services page. The **Virtual Common Audio Decoder Input Sources Ts Demux** table shows which SAT tuner each service uses by displaying "RF1" or "RF2" in the StrInfo column. This impacts the **RF Level**, **C/N**, and **TS Sync** values of the **Service Info** table.
      
  - **Audio Sources**: This page contains information and configurations of the device's Audio Sources. Currently available Audio Sources: RTP
    
  - **Settings**: Shows the settings available to the user. Currently it is possible to configure the SNMP Trap Destinations and XLR Channel Routing.
    
  - **Polling Config**: Data polling management page, where you can configure which polling groups should be polled. By default, they are all disabled.
    
  - **Web Interface**: The device's Web Interface, which is only accessible when the client machine has network access to the device.
    
