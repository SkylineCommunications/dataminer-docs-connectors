---
uid: Connector_help_Sencore_Impulse_300D_Decoder
---

# Sencore Impulse 300D Decoder

The **Impulse 300D Decoder** offers a large range of output ports including SDI, HDMI, and analog video with RCA stereo for legacy applications.

The **Sencore Impulse 300D Decoder** connector monitors and provides settings for the device. In range 1.0.x.x, SNMP and HTTP communication is used.

## About

### Version Info

| Range              | Key Features     | Based on | System Impact |
|--------------------|------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Initial version. | -        | -             |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | N/A                    |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Main connection (Range 1.0.0.x)

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination. Default: *80*.
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.
- **Number of Retries**: The number of retries for HTTP commands. This should be set to "0" for write parameters to work properly.
- **Timeout of a single command (ms)**: The time between HTTP commands. This should be set to "10000" for write parameters to work properly.

#### SNMP Connection (Range 1.0.0.x)

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **SNMP Type**: SNMPv2.
- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination. Default: *161*.
- **Bus address**: The bus address of the device (default: *ByPassProxy*).

SNMP Settings:

- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Initialization (Range 1.0.0.x)

On the **General > Authentication** page of the element, specify a username and password.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

The element created with this connector consists of the data pages detailed below.

### General
This page features information on the device, like its serial number and status code, as well as the authentication page necessary for the HTTP polling. 

### Inputs
This page features the current input that is active on the device, the status of each of the input types, and the pages for each of the input types (MPEG/IP, RTMP, HLS, SRT, ZIXI, CTP-Server)

### Decoding
This page shows the status of the currently selected service, its video details, and its audio details. It also has pages that shows each of the available services and the settings page that allows for changing the selected service. 

### Baseband Processing 
This page contains the tables for video configuration, captions/subtitles, compositing, and analog audio. 

### Baseband Outputs 
This page shows the settings put on the SDI Video. 

### Output
This page features the state, bitrate, and the IP transmit settings for the Output. 

### Admin 
This page features administration settings for the device including the Network, Date/Time, SNMP Communities, SNMP Trap Managers, and Syslog. 

### Health Status 
This page contains each of the alarming and events related tables including the Alarms, Traps, Event Logging, System Conditions, and System Events. 

## Notes 

This device requires both HTTP and SNMP connections due to some sets working through SNMP while others through HTTP. For example, for the "Select Input Type" on the "Inputs" page, most of the settings use SNMP for sets while the "None" setting uses HTTP due to how the connections were designed. 



