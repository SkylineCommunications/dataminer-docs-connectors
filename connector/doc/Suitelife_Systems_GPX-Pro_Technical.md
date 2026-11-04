---
uid: Connector_help_Suitelife_Systems_GPX-Pro_Technical
---

# Suitelife Systems GPX-Pro

## About

This connector monitors and controls a Suitelife Systems GPX-Pro through an MQTT broker, using the GPX-PRO MQTT API. It subscribes to the device topics under the configured GPX topic prefix, fills tables with the device channels, alarms, and connections, and publishes commands to the device when operators control relays or change channel settings.

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

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

### Redundancy

There is no redundancy defined.

## How to use

### General

This page shows the **Connection Status** with the broker, the **Reconnect Attempts**, and the device information: **Device State**, **Device Name**, **Device Model**, **Device Serial Number**, **Device Firmware Version**, **Device Free Storage**, **Uptime**, **Reboot Detected**, and **Reboot Count**.

- **Device State** is *Online* while the GPX publishes its heartbeat (every 30 seconds). It becomes *Offline* when the device's last will message arrives or when no device message has been received for about 90 seconds.
- **Reboot Detected** is set when the device uptime drops, and **Reboot Count** keeps the number of detected reboots across element restarts.
- If the connection to the broker is lost, the element reconnects automatically. Retries start after 10 seconds and double up to 5 minutes.

### Status Inputs

The **Status** table lists the GPX status channels. The **Value** is digital (0/1) and **Display** shows the configured on or off text.

You can edit **Label**, **Off Text**, **On Text**, and **GPX Channel**. The changes are sent to the device. Use the **Delete** button to remove a channel from the GPX.

### Analog Inputs

The **Analog** table lists the GPX analog channels, with their value, units, state, and minimum, maximum, and sample statistics.

You can edit **GPX Channel** and **Calibrate To**. In **Calibrate To**, enter the engineering value that the current reading should show. The connector calculates the calibration factor and sends it to the device. Use the **Delete** button to remove a channel from the GPX.

### Relays

The **Relay** table lists the GPX control channels. The **Mode** depends on **Pulse Ms**:

- If **Pulse Ms** is empty (or 0/1), the relay is latching. Use **Latch** (or the right-click menu) to switch it on or off.
- If **Pulse Ms** is 2 or higher, the relay is a pulse relay. Use **Pulse** to trigger it for that number of milliseconds.

**Control Busy** shows when a pulse is still active. New commands are blocked during that time, and **Last Control** shows the result of the last command.

### Connections

The **Connections** table lists the GPX connections (for example GPX, PING, and SNMP) with their online state.

### Advanced

- **SNMP**: Channels from the SNMP connection on the GPX.
- **Ping**: Channels from the PING connection on the GPX. You can edit **Host**, **Off Text**, and **On Text**. The changes are sent to the device.

Both tables have a **Delete** button to remove a channel from the GPX.

### Alarms

The **Alarms** table lists the active GPX alarms with their severity, value, and acknowledgment details. A row is removed when the alarm clears on the device.

Use **Acknowledge** to acknowledge one alarm, or **Acknowledge All Alarms** to acknowledge all unacknowledged alarms.

### Topics

The **Topics** table contains extra MQTT topics to subscribe to. Right-click the table to add or delete topics. Messages received on these topics are shown in the **Received Messages** table on the **Messages** page. The GPX topics are subscribed to automatically and are not listed here.

### Messages

The **Received Messages** table shows the messages received on the topics from the **Topics** table. With **Maximum Row Age** and **Max Rows**, you can limit how long and how many rows are kept. The **Output** parameter shows real-time connection information.

### Publish Data

To publish a message to the broker, fill in **Publish Topic** and **Publish Message**, and then click **Publish**.

### Diagnostics

This page shows the broker statistics from the broker's *$SYS/broker/#* topics. Enable **Broker Statistics** to fill this page. It is disabled by default because some brokers do not allow *$SYS* subscriptions.

## Notes

- Changes made in DataMiner are sent to the device. The table values update when the device publishes the new state.
- Deleting a channel in DataMiner removes it from the GPX device itself.