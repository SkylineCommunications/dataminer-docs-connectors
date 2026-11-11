---
uid: Connector_help_Suitelife_Systems_GPX-Pro_Technical
description: "Configure the Suitelife Systems GPX-Pro connector in DataMiner: MQTT broker setup, channel tables, relay control, and device alarms."
---

# Suitelife Systems GPX-Pro

## About

This connector monitors and controls a Suitelife Systems GPX-Pro (GPX-8 Pro and GPX-32 Pro) through an MQTT broker, using the GPX-Pro MQTT API. It subscribes to the device topics under the configured GPX topic prefix, fills tables with the device channels, alarms, and connections, and publishes commands to the device when operators control relays or change channel settings.

All device data is exchanged over MQTT. The element also has an HTTP connection, but this connection is **only used to open the device web interface** on the **Web Interface** page. No data is polled over HTTP.

### Architecture

The GPX-Pro does not communicate with DataMiner directly. Both the device and the DataMiner element connect as clients to the same MQTT broker:

1. The GPX-Pro publishes its state, channel configuration, alarms, and heartbeat to the broker under its topic prefix.
1. The DataMiner element subscribes to these topics and updates its tables in near real time.
1. When an operator changes a setting or controls a relay, the element publishes a command to the broker, and the GPX-Pro picks it up.

[Eclipse Mosquitto](https://mosquitto.org/) is the recommended broker. It is free, runs on Windows and Linux, and uses very few resources. It can be installed on the DataMiner Agent or on a separate server, as long as both the GPX-Pro and the DataMiner Agent can reach it.

### Supported devices

| Model | Channels | Firmware |
|--|--|--|
| GPX-8 Pro | 8 | 3.0.x |
| GPX-32 Pro | 32 | 3.0.x |

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection that is only used for the **Web Interface** page. It requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The IP address of the GPX-Pro device.
- **IP port**: The port of the device web interface, by default *80*.
- **Bus address**: By default *ByPassProxy*.

> [!NOTE]
> The MQTT broker settings are not configured during element creation. Configure them on the **Configuration** page after the element has been created (see [Initialization](#initialization)).

### Broker and device preparation

Before you create the element:

1. Install an MQTT broker, for example Mosquitto, and make sure its listener port (by default *1883*, or *8883* for TLS) is reachable from both the GPX-Pro and the DataMiner Agent. From Mosquitto 2.0 onwards, a `listener` must be configured explicitly to accept remote connections, and either `allow_anonymous true` or a password file must be set.
1. In the GPX-Pro web interface, enable MQTT, enter the broker address and credentials, and note the **topic prefix** (for example *fox/gpx32*). You will need this prefix in DataMiner.
1. Optionally, allow subscriptions to the *$SYS/#* topics on the broker if you want to see broker statistics in DataMiner.

### Initialization

After you create the element, configure the following parameters on the **Configuration** page, and then click **Connect**:

- **Broker Hostname** and **Broker Hostname Port**: The hostname or IP address and the TCP port of the MQTT broker.
- **Client ID**: Optional. Must be unique on the broker. If this is empty, *dm-[DMA ID]-[element ID]* is used.
- **Username** and **Password**: The credentials for the broker, if it requires authentication.
- **TLS Method**:
  - *None*: No TLS. Not recommended.
  - *Server*: The connection is encrypted with the server certificate. The server CA must be trusted on the DataMiner Agent.
  - *Mutual*: Server TLS plus a client certificate. Configure **Certificates Folder**, **CA Certificate**, **Client Certificate**, and **Client Certificate Password** on the **Client TLS** subpage.
- **GPX Topic Prefix**: The MQTT topic prefix configured on the GPX device (for example *fox/gpx32*). While this is empty, no GPX topics are subscribed to or published.

### Web Interface

The **Web Interface** page opens the GPX-Pro web interface, using the IP address and port of the HTTP connection.

The web interface is only accessible when the client machine has network access to the product.

## How to Use

The connector communicates with the broker from within QActions. As a result, no MQTT traffic is shown in the Stream Viewer. Use the **Diagnostics** page and the element log file to troubleshoot the communication.

### Device status

The **General** page shows the **Connection Status** with the broker and the device information, such as **Device State**, **Device Firmware Version**, and **Uptime**.

- **Device State** is *Online* while the GPX publishes its heartbeat (every 30 seconds). It becomes *Offline* when the device's last will message arrives or when no device message has been received for about 90 seconds.
- If an established connection to the broker is lost, the element reconnects automatically. Retries start after 10 seconds and double up to 5 minutes.

### Monitoring channels

- **Relays**: The GPX control channels, with their state and mode.
- **Status Inputs**: The GPX status channels. The **Value** is digital (0/1), and **Display** shows the configured on or off text.
- **Analog Inputs**: The GPX analog channels, with their value, units, state, and minimum, maximum, and sample statistics.
- **Connections**: The GPX connections (for example GPX, PING, and SNMP) with their online state.
- **Advanced**: The channels of the SNMP and PING connections on the GPX.

### Controlling relays

The **Mode** of a relay depends on **Pulse Ms**:

- If **Pulse Ms** is empty, 0, or 1, the relay is latching. Use the **Latch** buttons to switch it on or off.
- If **Pulse Ms** is 2 or higher, the relay is a pulse relay. Use the **Pulse** button to trigger it for that number of milliseconds.

All relay commands ask for confirmation before they are sent.

### Changing channel settings

You can change the following settings in the tables. The changes are sent to the device:

- **Relays**: **Pulse Ms** and **GPX Channel**.
- **Status Inputs**: **Label**, **Off Text**, **On Text**, and **GPX Channel**.
- **Analog Inputs**: **GPX Channel** and **Calibrate To**. In **Calibrate To**, enter the engineering value that the current reading should show. The connector calculates the calibration factor and sends it to the device.
- **Ping** (on the **Advanced** page): **Host**, **Off Text**, and **On Text**.

Use the **Delete** button in a row to remove that channel from the GPX device.

### Handling device alarms

The **Alarms** table lists the active GPX alarms with their severity, value, and acknowledgment details. A row is removed when the alarm clears on the device.

Use **Acknowledge** to acknowledge one alarm, or **Acknowledge All Alarms** to acknowledge all unacknowledged alarms.

### Diagnostics

The **Diagnostics** page shows the broker statistics from the broker's *$SYS/broker/#* topics. Enable **Broker Statistics** to fill these parameters. This is disabled by default because some brokers do not allow *$SYS* subscriptions.

From this page, you can also open the following subpages:

- **Topics**: Extra MQTT topics to subscribe to. Right-click the table to add or delete topics. The GPX topics are subscribed to automatically and are not listed here.
- **Messages**: The messages received on the topics from the **Topics** table. With **Maximum Row Age** and **Max Rows**, you can limit how long and how many rows are kept.
- **Publish Data**: Fill in **Publish Topic** and **Publish Message**, and then click **Publish** to publish a message to the broker.

## Notes

- The HTTP connection is only used for the **Web Interface** page. All monitoring and control goes through the MQTT broker.
- If the broker cannot be reached when the element starts, the element does not retry automatically. Click **Connect** on the **Configuration** page once the broker is available.
