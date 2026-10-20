---
uid: Connector_help_Sencore_SMD989_Technical
---

# Sencore SMD989

## About

This is a DataMiner connector for the **Sencore SMD-989**, a DVB-S/S2/S2X/TurboPSK modulator, used to monitor and configure the device over **SNMP**.

## Configuration

### Connections

#### SNMP Connection - Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **IP port**: The IP port of the device.
- **Get community string**: The community string used when reading values from the device (default: *public*).
- **Set community string**: The community string used when setting values on the device (default: *private*).

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### System Page

This page contains system info parameters, including:

- **Unit 10 MHz Reference Clock**: Indicates whether the system is using an **external** or **internal** 10 MHz reference clock.
- **Unit 10 MHz External Reference Clock Error**: Signals whether an error was encountered with the reference clock (possible values: *OK* or *Fail*).
- **Unit Mute on Settings Change**: If this is *Enabled*, the connector automatically mutes the output(s) on a modulation or output setting change. Output(s) are muted only on the bay where the change occurred. If this is *Disabled*, each output mute setting retains its configured value on a modulation or output setting change.

The page also contains page buttons to the [**Network Settings**](#network-settings-subpage), [**Clone Settings**](#clone-settings-subpage), and [**License Settings**](#license-settings-subpage) subpages.

#### Network Settings Subpage

This subpage contains the following tables:

- **MPEG IP table**: Displays the connector to use as **Default Gateway** (*Connector 1* or *Connector 2*), and allows you to enable or disable the **ICMP Response**.

- **MPEG IP NIC table**: Includes the following parameters:

  - **IP Address**: The IP address of the MPEG NIC.
  - **Subnet Mask**: The subnet mask of the MPEG NIC.
  - **Gateway**: The gateway of the MPEG NIC.
  - **MAC**: The MAC address of the MPEG NIC.
  - **Link Speed**: The link speed, expressed in **Mbps**, of the MPEG NIC.
  - **Link Status**: The link status of the MPEG NIC (*Down*, *Half Duplex*, or *Full Duplex*).
  - **Rx Rate**: The aggregated received bitrate, expressed in **Mbps**.
  - **IGMP**: Detected IGMP protocol version used in the network (*Version 1*, *Version 2*, or *Version 3*).

#### Clone Settings Subpage

This subpage contains the following parameters:

- **Cloning**: Allows you to enable or disable the clone settings.
- **Remote Unit Address**: The IP address of the unit to clone the settings from.
- **Public SNMP Community**: The SNMP community string used to access the remote unit.

#### License Settings Subpage

This page contains the **Bay License table**, which includes the following parameters:

- **Name**: The license option name.
- **Bay Assignment**: The licensing bay assignment (*Bay 1*, *Bay 2*, or *Bay 1 / Bay 2*).

### Input Page

#### Information Parameters

This page contains the following information parameters:

- **Primary Input**: The primary input source for the stream. Refer to the **Label** values from the [**Input table**](#input-table).
- **Backup Input**: The backup input source for the stream. Refer to the **Label** values from the [**Input table**](#input-table). However, note that input failover is not supported when the DVB-S2 multi-stream modes are used.
- **Failover Condition**: The condition that triggers failover of the stream input from the primary input source to the backup input source. However, note that input failover is not supported when the DVB-S2 multi-stream modes are used.
- **PRBS Status**: Allows you to enable or disable PRBS (pseudo-random binary sequence) as the modulator input.
- **Restore Condition**: Condition that triggers the stream input to switch back from the backup input source to the primary input source. However, note that input failover is not supported when the DVB-S2 multi-stream modes are used.

The possible values of the **Failover Condition** parameter depend on the value of the **Restore Condition** parameter, and vice versa.

- If the value of the **Restore Condition** parameter is not *Manual Only*, the **Failover Condition** parameter can be set to anything except *Manual Only*.
- If the value of the **Failover Condition** parameter is *Manual Only*, the only valid value of the **Restore Condition** parameter is *Manual Only*.
- If the value of the **Restore Condition** parameter is *On Primary TS Restored* or *On Backup TS Loss*, the only valid value for the **Failover Condition** parameter is *On Primary TS Loss*.
- Similarly, if the value of the **Restore Condition** parameter is *On Primary TS Analysis Restored* or *On Backup TS Analysis Failure*, the only valid value for the **Failover Condition** parameter is *On Primary TS Analysis Failure*.
- If the value of the **Failover Condition** parameter is *On Primary TS Loss*, then the valid values of the **Restore Condition** parameter are *On Primary TS Restored* and *On Backup TS Loss*.
- Similarly, if the value of the **Failover Condition** parameter is *On Primary TS Analysis* *Failure*, then the valid values of the **Restore Condition** parameter are *On Primary TS Analysis Restored* or *On Backup TS Analysis Failure*.

#### Input Table

The page also displays the **Input table**, which includes the following parameters:

- **Label**: Label of the input.
- **Bitrate**: The calculated bit rate of the stream, expressed in **Mbps**.
- **Status**: Allows you to determine whether or not the input is **enabled**.

#### IP Settings Subpage

Finally, the **Input** page also contains a page button to the **IP Settings** subpage.

This subpage contains two tables:

- The **MPEG IP Rx** table includes the following parameters:

  - **IP Address**: The multicast destination group address.
  - **Destination Port**: The multicast destination group port.
  - **IGMP Mode**: The source filter list mode (possible values: *Include* or *Exclude*).
  - **Protocol**: The packet protocol (possible values: *UDP* or *RTP*).
  - **TS Packets per IP**: The number of transport stream packets per IP packet.
  - **Buffer Size**: The receive buffer size, expressed in **KB**, for the MPEG IP stream.
  - **Buffer Delay**: The buffer latency, expressed in **ms**.
  - **Routing Mode**: Allows you to configure the stream to use **unicast** or **multicast** routing.
  - **SSRC Filter Mode**: Configures the enabled state of SSRC source filtering.
  - **SSRC Filter Value**: Configures an SSRC value to use as a source filter.
  - **Out Of Order Packets**: The number of out-of-order packets received in the stream.
  - **Duplicate Packets**: The number of duplicate RTP packets received.
  - **Lost Packets**: The number of missing packets according to the RTP sequence counter.
  - **Corrected Packets**: The number of correctable FEC errors detected in the stream.
  - **Uncorrected Packets**: The number of uncorrectable FEC errors detected in the stream.
  - **FEC State**: Configures the **enabled** state of processing FEC data for the stream.
  - **FEC Rows**: The number of rows detected in the FEC data for the IP stream.
  - **FEC Columns**: The number of columns detected in the FEC data for the IP stream.
  - **FEC Corrected per Period**: The number of correctable FEC errors per FEC period detected in the stream.
  - **Connector**: The port used (*Port 1* or *Port 2*).
  - **Buffer Mode**: Allows you to choose the size, expressed in **kB**, or delay, expressed in **ms**.
  - **Buffer Delay Target**: The receive buffer size, expressed in ms, for the MPEG IP stream.
  - **FEC Mode**: The current FEC mode (possible values: *Disabled*, *Columns Rows*, *Columns*, or *Not Present*).

- The **MPEG IP IGMP** table includes the following parameters:

  - **Address Type**: *IPv4*, *IPv6*, *IPv4-Z*, *IPv6-Z*, or *DNS*.
  - **IP Address**: The IGMP source filter address.
  - **Row Status**: The row status for the IGMP source filter address (*Active*, *Not in Service*, *Not Ready*, *Create And Go*, *Create And Wait*, or *Destroy*).

### Modulator Page

This page contains the following information parameters:

- **Symbol Rate**: Allows you to configure the modulation symbol rate in **Msymps**. Used only if the mod rate mode is set to symbol rate.
- **DVB-S2 Frame Size**: Allows you to select **normal** or **short** frames. Some combinations of stream mod type code rate and DVB-S2 frame size are invalid.
- **Modulation Mode**: Allows you to select the modulation mode (*DVB-S2 Single-CCM*, *DVB-S2 Multi-CCM*, *DVB-S2 Multi-VCM*, *DVB-S/DSNG*, *TurboPSK*, or *DVB-S2X Single-CCM*).
- **Spectral Inversion**: Allows you to enable spectral inversion (possible values: *Normal* or *Inverted*).
- **Filter Roll Off**: Allows you to select the roll-off value. The **15%**, **10%**, and **5%** roll-off values are valid only in DVB-S2 Single-CCM or TurboPSK modulation mode.
- **DVB-S Type Code Rate**: The selected modulation scheme and code rate for DVB-S.
- **Rate Adaptation**: Allows you to enable or disable the S2 single stream rate adaptation.
- **DVB-S2 PL Scramble Code**: Allows you to set the physical layer scrambling code. A value of "0" resets it to the default broadcast value.

The **Modulator** page also contains buttons to the [**Carried ID**](#carried-id-subpage), [**PRBS**](#prbs-subpage), and [**TS Analysis**](#ts-analysis-subpage) subpages.

#### Carried ID Subpage

This subpage contains the following parameters:

- **Global Unique ID**: The globally unique identifier of the bay. In version 1, this is defined as the unit's MAC address, with a CRC-8 value prepended.
- **Transmission Mode**: Allows you to enable or disable the transmission of the carrier ID.
- **Latitude Transmission**: Allows you to enable or disable the transmission of the latitude in the carrier ID.
- **Latitude**: The latitude of the unit, expressed in **0.0001 decimal degrees** (+XXX north / -XXX south).
- **Longitude Transmission**: Allows you to enable or disable the transmission of the longitude in the carrier ID.
- **Longitude**: The longitude of the unit, expressed in **0.0001 decimal degrees** (-XX west / +XX east).
- **Telephone Transmission**: Allows you to enable or disable the transmission of the telephone number in the carrier ID.
- **Telephone**: The contact telephone number to be transmitted. Use "x" as a delimiter between the number and the extension.
- **User Transmission**: Allows you to enable or disable the transmission of the user data in the carrier ID.
- **User**: User data to be transmitted. A message of up to 24 ASCII characters can be entered here.

#### PRBS Subpage

On this subpage, you can set the **PRBS Mode**, the mode you use when PRBS (pseudo-random binary sequence) is enabled (possible values: *PN 23 Normal* or *PN 23 Inverted*).

#### TS Analysis Subpage

This subpage displays the **TS Analysis table**, which contains the following parameters:

- **State**: Allows you to enable or disable the TS Analysis block. Only available in DVB-S/DSNG (Single) or DVB-S2 CCM (Single) modulation mode.
- **Sync Byte Threshold**: The sync byte threshold, expressed in errors/s, with a range of 1 to 999.
- **PAT Error Threshold**: The PAT error threshold, expressed in ms, with a range of 100 to 10000.
- **CC Error Threshold**: The CC error threshold, expressed in errors/s, with a range of 1 to 999.
- **PMT Error Threshold**: The PMT error threshold, expressed in ms, with a range of 100 to 10000.
- **ES PID Error Threshold**: The ES PID error threshold, expressed in ms, with a range of 100 to 10000.
- **Null Packet Ratio Threshold**: The greatest percentage of null packets to total packets that will not trigger an error.

### Output Page

This page contains the following parameters:

- **Frequency**: Allows you to change the IF output frequency (**MHz**) with a range of 50 to 180.
- **Level**: Allows you to configure the IF output level. The range for the standard modulator is -30 to -5 **dBm**. The range for the high-power modulator is -20 to 5 **dBm**.
- **Tilt**: The amount of tilt applied across the active bandwidth, expressed in **dB**.
- **Mode**: Allows you to enable or disable the modulator's IF output signal.
- **IQ Calibration Finished**: Indicates when the calibration is finished.

### Web Interface Page

This page displays the web interface of the device. Note that the client machine has to be able to access the device, as otherwise it will not be possible to open the web interface.
