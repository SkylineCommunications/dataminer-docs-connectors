---
uid: Connector_help_CISCO_Catalyst_SD-WAN_Technical
---

# CISCO Catalyst SD-WAN

## About

This is a DataMiner connector for the **CISCO Catalyst SD-WAN** (Software-Defined WAN), a software-based Wide Area Network management solution developed by CISCO with integrated capabilities for multicloud, security, predictive operations, and enhanced network visibility on a SASE-enabled architecture.

This connector connects to the solution using an HTTP connection and displays various information, including connected devices, their respective sites and tunnels, network health, certificates data, and alarms.

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Bus address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Authentication

When you have created the element, go to the **General** > **Authentication** page, fill in the Catalyst Manager REST API credentials in the **Username** and **Password** fields to authenticate with the device, and click **Login**.

The **Connection Status** parameter will then display whether the connection was successful:

- **Authentication Failed**: The connector had an issue while authenticating. It may be that the credentials used were incorrect. The connector will not be authenticated in this way, and manual reauthentication is necessary in order to retrieve information.

- **Connected**: The connector's authentication process was successful. The connector will continue to have this status until either a manual or automatic disconnection ensues.

### Polling Manager

While in the **Connected** state, the connector will be able to fetch information to display in the element. The requested data is determined by the configuration on the **Polling Manager** page.

On that page, you can configure which data will be polled and at which time interval. By default, the polling of each data module will start off as **Enabled**. You can also individually force the polling or reset the polling interval to its default value.

### Element Settings

On the **Element Settings** page, you can configure additional, optional settings for the element:

- **Try to Connect on Startup**: When the element restarts, if there are saved credentials on the **Authentication** page, the element can try to connect automatically using those credentials without the need for the user to manually log in again. This functionality is enabled by default.

- **Automatic Reconnection**: If an unexpected disconnection occurs, for example in case the stored authentication token expires, the element can try to reconnect automatically instead of waiting for user input to try to reauthenticate. This functionality is enabled by default.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### Health Data

The network's health data can be seen as pie charts on the **General** page, replicating the web interface UI's presentation with the number of objects by their health quality (*Poor*, *Fair*, and *Good*). To see the raw data these charts are based on, go to the **Health Data** subpage.

### Devices

The **Devices** page lists the devices with their hostnames, IPs, health and reachability status, and CPU/memory usage data.

### Sites

The list of sites is available on the **Sites** page, and includes the respective site names, health data, and latitude/longitude values indicating the physical locations.

### Certificates

The **Certificates** page lists all the certificates, their respective serial numbers, expiration dates, and status.

### Alarms

The **Alarms** page displays information on the CISCO Catalyst SD-WAN's alarms. You can select to see all alarms or only active alarms. The displayed information includes the severity, source, alarm message, and alarm entry time.

### Control Connections

On the **Control Connections** page, both the host and the peer's detailed information will be displayed, including their control connection protocol, public and private identifiers, and peer type.

> [!NOTE]
> Fetching this data is only possible if the polling of the devices is enabled. The polling manager should automatically prevent enabling the polling of this data if its dependency is disabled.

### Tunnels

The network's tunnels are listed on the **Tunnels** page. The information displayed here includes the tunnels' source and destination information (including Transport Location (TLOC) Color), encapsulation type, average statistics, and the total transmission/reception octets.

> [!NOTE]
> Fetching this data is only possible if the polling of the devices is enabled. The polling manager should automatically prevent enabling the polling of this data if its dependency is disabled.

### BFD Sessions

BFD sessions are listed on the **BFD Sessions** page, with each session's source and destination information (including Transport Location (TLOC) Color), encapsulation type, and session state.

> [!NOTE]
> Fetching this data is only possible if the polling of the devices is enabled. The polling manager should automatically prevent enabling the polling of this data if its dependency is disabled.

### BGP Neighbors

The BGP neighbors pairs of devices are shown on the **BGP Neighbors** page. The information displayed here includes the pair's information, the Address Family Identifier and Subsequent Address Family Identifier, the VPN Identifier, and the number of received and sent messages that were open.

> [!NOTE]
> Fetching this data is only possible if the polling of the devices is enabled. The polling manager should automatically prevent enabling the polling of this data if its dependency is disabled.
