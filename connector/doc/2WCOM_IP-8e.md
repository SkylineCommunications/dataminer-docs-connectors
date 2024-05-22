---
uid: Connector_help_2WCOM_IP-8e
---

# 2WCOM IP-8e

The 2WCOM IP-8e is a point-to-point or point-to-multipoint audio encoder using IP-based audio network technologies for real-time streaming.

## About

### Version Info

| Range | Key Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x | Initial version. | - | - |
| 1.0.1.x [Obsolete] | - DataMiner Connectivity Framework (DCF) integration added. <br>- Redundant polling added. | 1.0.0.1 | - DCF can cause an additional load on the system. <br>- Existing elements need to be reconfigured to use the redundant connection. |
| 2.0.0.x [Main range] | Conversion of connector from SNMP to HTTP connection. | 1.0.1.1      | Existing elements need to be reconfigured to use HTTP connection instead of SNMP. |

### Product Info

| Range              | Supported Firmware |
|--------------------|--------------------|
| 1.0.0.x            | 2.11.12            |
| 1.0.1.x [Obsolete] | 2.11.12            |
| 2.0.0.x            | 2.15               |

### System Info

| Range              | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|--------------------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x            | No              | Yes                 | -                 | -                   |
| 1.0.1.x [Obsolete] | Yes             | Yes                 | -                 | -                   |
| 2.0.0.x            | Yes             | Yes                 | -                 | -                   |

## Configuration

### Connections

This connector uses HTTP connections and requires the input detailed below during element creation.

### HTTP Connection - Primary

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: 80).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.
- **Timeout of a single command**: The default timeout time is 5000 ms, as there are API calls that usually take around 3-4 s to respond. If you notice timeout alarms or the element switching between primary and secondary connection, increase this timeout time.

### HTTP Connection - Secondary

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: 80).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.
- **Timeout of a single command**: The default timeout time is 5000 ms, as there are API calls that usually take around 3-4 s to respond. If you notice timeout alarms or the element switching between primary and secondary connection, increase this timeout time.

### Initialization

On the **Login** page, log in using the same credentials as for the web interface of the device.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

### Redundancy

The element is configured with a redundant connection. When the primary connection is no longer responding (i.e. a timeout occurs on this connection), DataMiner will automatically switch to the secondary connection (and vice versa).

## How to use

This connector uses HTTP parameters to access and modify the device parameters.

The connector uses a UI structure similar to the web interface of the device. You can also control the parameters in a similar way.

To add new multiplexers, you will need to use the web interface of the device (available on a page of the element). These will then be accessible only through the web interface of the device.

The connector does not provide access to sensitive information such as the User, Storage, or Log pages of the web interface.
#### Poll Manager

With the poll manager, you can enable or disable polling commands, as well as change the poll interval (within certain limits).
By default, all commands are enabled.

Below, you can find a list of existing commands and the information (tables and parameters) they poll.

| Command/Name | Polled Tables | Polled Parameters |
|--|--|--|
| VirtCsl/Device Status | Device Fans<b>GPI States<b>GPO States  | General parameters<b>Mainboard parameters |
| Csl/Device Settings | External APIs<b>GPO Configuration<b>syslog Settings | Headphone<b>External APIs<b>NTP \[Network Settings\] |
| VirtCsl/Monitoring Status | AES/EBU and Silence Detection Statuses<b>No Input Data Encoder Statuses<b>Ancillary Data Statuses<b>LAN Data Links Statuses | NTP Clock Status<b>Temperature Status<b>Power Supply Status<b>LAN Ctrl Link Status |
| Csl/Monitoring Settings | LAN Data Links<b>AES/EBU No Signal Audios<b>AES/EBU Silence Detection Audios<b>AES/EBU CRC Error Audios<b>No Input Data Encoders<b>Ancillary Timeout Audios<b>DTE Timeout Inputs | Externa; Clock NTP Parameters<b>Device Hardware Parameters<b>Network LAN Ctrl |
| VirtCsl/External Clock Sources | N/A | NTP Statuses |
| Csl/Audio Clock | External Audio Clocks | External Clock (PTP and NTP) |
| Csl/Interface | Ancillary Data DTE Inputs | Audio Device Mode<b>Critical Level Marker Digital & Analog Threshold |
| Csl/Decoder Input Sources File | File Input Sources | Check Criteria - File |
| Csl/Decoder Input Sources RTP | ES-RIST Input Sources | Check Criteria - ES-RIST |
| Csl/Decoder Input Sources ICY | Icecast Input Sources | Check Criteria - Icecast |
| Csl/Decoder Input Sources XLR | XLR Input Sources | Check Criteria - XLR |
| VirtCsl/IP Config VLANs | Interface Settings Table<b>MAC Addresses<b>Ctrl VLANs<b>Data 1 VLANs<b>Data 2 VLANs | N/A |
| Csl/IP Config Interface Services | VLANs and DNSs<b>Ctrl Interface Services<b>Data 1 Interface Services<b>Data 2 Interface Services<b>Interface Services | DNS Routing |
| VirtCsl/Interface Ethernet Status | Ethernet Statuses | N/A |
| VirtCsl/Ancillary Data | DTE Inputs | N/A |
| Csl/FPGA Encoder Config | Audio Inputs<b>Analog Signal Types<b>Analog Volumes<b>Digital Volumes | N/A |
| Csl/Ancillary Data Input | Ancillary Data UDP Inputs | N/A |
| Csl/Encoder Outputs | ES-RIST Encoder Outputs<b>Icecast Source Client Encoder Outputs<b>Icecast Server Encoder Outputs | Table Status (Icecast Server Encoder Outputs)<b>Table Status (Icecast Source Client Encoder Outputs)<b>Table Status (ES-RIST Encoder Outputs) |
| VirtCsl/Encoder Outputs Control | Encoder Outputs Control | N/A |
| VirtCsl/Decoder Input Sources | Input Sources Control | N/A |
| Csl/Audio Profiles | Audio Profiles | N/A |
| Csl/Decoder Input Sources Livewire | Livewire Input Sources | N/A |
| Csl/Input Sources Livewire Check Criteria | N/A | Check Criteria - Livewire |
