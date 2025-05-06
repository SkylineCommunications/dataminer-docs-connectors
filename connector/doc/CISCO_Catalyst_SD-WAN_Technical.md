---
uid: Connector_help_CISCO_Catalyst_SD-WAN_Technical
---

# CISCO Catalyst SD-WAN

## About

This is a DataMiner connector for the **CISCO Catalyst SD-WAN** (Software-Defined WAN), a software-based Wide Area Network management solution developed by CISCO with integrated capabilities for multicloud, security, predictive operations, and enhanced network visibility on a SASE-enabled architecture.
This driver connects to the solution by an HTTP connection and displays various information, including connected Devices, their respective Sites and Tunnels, Network Health, Certificates data and Alarms.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- IP address/host: The polling IP or URL of the destination.
- IP port: The IP port of the destination.
- Bus address: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

The **Authentication** subpage, which can be accessed through the **General** page, contains the fields **Username** and **Password** used to authenticate the user to the device. These fields must be filled in with the Catalyst Manager REST API credentials in order for the connector to be able to retrieve information.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### Authentication and Configuration

After introducing the Catalyst Manager REST API credentials on the **Authentication** subpage and clicking the **Login** button for the first time, there are two possible outcomes to the authentication request, displayed on the **Conncetion Status** parameter; Connected, or Authentication Failed.

- **Authentication Failed**: The connector had an issue while authenticating. It may be that the credentials used were incorrect. The connector will not be authenticated in this way, and manual reauthentication is necessary in order to retrieve information.

- **Connected**: The connector's authentication process was successful. The connector will continue to be in this status until either a manual or automatic disconnection ensues.

While in the **Connected** status, the connector will be able to fetch the necessary information in order to populate itself. What data is requested is defined in the page **Polling Manager**.
In this page, you will be able to configure what data will be polled, and by which time interval. By default, the polling of each Data Module will start off as **Enabled**. You can also individually force poll or reset the polling interval to its default value.


#### Additional Configuration (Optional)

In the page **Element Settings**, additional configurations can be changed.

- **Try to Connect on Startup**: On element restart, if there are saved credentials on the **Authentication** page, the element can try to connect automatically using those credentials without the need for the user to click the **Login** button again. This functionality is enabled by default.

- **Automatic Reconnection**: If an unexpected disconnection occurs, as it is in the case of the stored authentication token expiring, the element can try to reconnect automatically instead of waiting on user input to try to re-authenticate. This functionality is enabled by default.

### Health Data

The network's health data can be seen as pie charts in the **General** page, replicating the Web Interface UI's presentation with the number of objects by their health quality (Poor, Fair and Good). Their respective raw data can be seen in the tables under the subpage **Health Data**.

### Devices

In the **Devices** page, the devices are listed, including their hostnames, IPs, health and reachability status, and CPU/Memory usage data.

### Sites

The list of sites is available under the page **Sites**, which includes their respective site names, health data, and latitude/longitude values indicating their physical locations.

### Certificates

The certificates can be seen in page **Certificates**. This page includes the listing of all certificates, their respective serial numbers, expiration dates and status.

### Alarms

Information on the CISCO Catalyst SD-WAN's Alarms is displayed on the **Alarms** page. Here it is possible to choose to see all or only active alarms, which include information about the alarm's severity, source, alarm message, and alarm entry time.

### Control Connections

Control connections are displayed in the **Control Connections** page. Here, both the host and the peer's detailed information should be displayed, including their control connection protocol, public and private identifiers, and peer type.

> [!NOTE]
> Fetching this data is only possible if the polling of the Devices is enabled. The polling manager should automatically prevent enabling the polling of this data if its dependency is disabled.

### Tunnels

The network's tunnels are listed in the page **Tunnels**. Some information displayed here includes the tunnel's source and destination information (including Transport Location (TLOC) Color), encapsulation type, average statistics, and the total transmission/reception octets.

> [!NOTE]
> Fetching this data is only possible if the polling of the Devices is enabled. The polling manager should automatically prevent enabling the polling of this data if its dependency is disabled.

### BFD Sessions

BFD Sessions are listed under the **BFD Sessions** page, which show each session's source and destination information (including Transport Location (TLOC) Color), encapsulation type, and session state.

> [!NOTE]
> Fetching this data is only possible if the polling of the Devices is enabled. The polling manager should automatically prevent enabling the polling of this data if its dependency is disabled.

### BGP Neighbors

The BGP neighbors pairs of devices are shown on the page **BGP Neighbors**. Information displayed here includes the pair's information, Address Family Identifier and Subsequent Address Family Identifier, VPN Identifier, and the number of received and sent messages that were open.

> [!NOTE]
> Fetching this data is only possible if the polling of the Devices is enabled. The polling manager should automatically prevent enabling the polling of this data if its dependency is disabled.

