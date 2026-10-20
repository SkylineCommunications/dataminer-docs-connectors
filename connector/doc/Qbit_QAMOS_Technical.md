---
uid: Connector_help_Qbit_QAMOS_Technical
---

# Qbit QAMOS

## About

QAMOS is Qbit's broadcast monitoring system designed for modern, IP-based workflows. It provides browser-based control room views with visualization of audio levels and signal metrics, supports end-to-end monitoring across multiple signal types (Icecast, HLS, MPEG-2 TS, EDI, and AES67), and enables multi-input recording of audio and bitstreams for post-event analysis and troubleshooting.

This connector uses the QAMOS REST API to monitor and control the device.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

Once the element has been created, go to the **General** page and open the **Authentication** subpage. Fill in the **Username** and **Password** of a QAMOS user and click the **Login** button to retrieve a JWT bearer token. The **Authentication State** parameter reflects the result of the login attempt (*Logged In*, *Logged Out*, *Token Expired*, or *Login Failed*). The connector automatically refreshes the token when it expires, as long as valid credentials are configured.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector polls the QAMOS REST API to retrieve device information and to apply user changes. To inspect data traffic, you can enable and consult the **HTTP DEBUG** page.

The element has the following data pages:

- **General**: Shows system information (name, location, contact, hostname, firmware version and build) and system health (CPU load, memory usage, uptime, boot time). The **Authentication** subpage is used to log in to the device.
- **Interfaces**: Shows the status of the network interfaces (address, netmask, gateway, link, state, speed, TX/RX rate) and allows the network interface configuration (DHCP, IP, DNS, HTTP proxy, role assignment) to be changed.
- **Inputs**: Lists all configured inputs with their source type, enabled state, and the linked measurement profile. Dedicated subpages are available per source type:
  - **Inputs - Icecast**
  - **Inputs - HLS**
  - **Inputs - MPEG-2 TS** (with an MPEG-2 TS service list subpage)
  - **Inputs - EDI** (with an EDI service list subpage)
  - **Inputs - AES67**
- **Streams**: Lists the streams derived from the inputs, including codec, bitrate, audio buffer fill, channel count, sample rate, and HLS/Icecast-specific metrics.
- **Measurement Profiles**: Lists the measurement profiles and exposes the configuration of loudness, input loss, silence detection, AES67 invalid SDP, HLS invalid playlist, HLS playlist size, HLS playlist update interval, and EDI no superframe sync alarms.
- **Taps**: Shows the Icecast and HLS taps that are exposed by the device for monitoring outputs.
- **Active Alarms**: Lists the currently firing alarms with priority, type, source, message, and start/ack/end times. Each entry can be acknowledged from the table.
- **Past Alarms**: Lists historical alarms. The maximum number of polled entries can be configured, and an action is available to clear all past alarms.
