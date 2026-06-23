---
uid: Connector_help_Telenet_CM_Collector
---

# Telenet CM Collector

The **Telenet CM Collector** is part of the EPM solution deployed at Telenet, and works together with the **Telenet CPE Manager**, **Telenet STB Collector** and **Telenet eMTA Collector** connector. This connector is responsible for the polling cable modems.

## About

This connector will poll all the CMs in two poll cycles:

- Fast Poll: Polling CMs over a 15-minute period.
- Slow Poll: Polling CMs over a 24-hour period.

In addition, there is another poll cycle that will poll the CMTS to request the US data of all the CMs over a 15-minute period. The polled data will be offloaded into CSV files and will be aggregated by the CPE Manager element. The CPE Manager element will provision the CM Collector with the CMs that need to be polled and their IP addresses. The CM Collector will send traps towards Adlex Nouveau.

## Installation and configuration

### Creation

This connector uses two Simple Network Management Protocol (SNMP) connections. The first SNMP connection is used to connect to the CM and the second one to connect to the CMTS.

The following input is required during element creation:

**SNMP Connection:**

- **IP address/host**: 127.0.0.1 (IP addresses will be dynamically filled in).
- **Device address**: Not needed.

**SNMP Settings:**

- **Port Number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: Not needed, because the connector will not perform sets.

Note: All polled CMs will share the same settings, and all polled CMTSs will share the same settings.

### Configuration of the offload parameters

The CM Collector's data display pages are not intended to be opened. Instead the configuration should be performed either through a multiple set or via a Visio file.

The parameter **Data Offload Folder** contains the location of the fast and slow offload files. To find the location where the HGW files are offloaded, go one level higher in the folder structure, and check the HGW directory. The parameter **RCCV Data Offload Folder** contains the location of the IVR files.

### Configuration of the threshold parameters

The threshold parameters are used during aggregation. If the parameter in the CPE manager is %CM With DS SNR \< T, then the DS SNR parameter is compared with the DS SNR Low Threshold. If the SNR is below the value in the configuration parameter, then the CM is taken into account.

The following parameters can be configured: **DS CR High Threshold, DS CS High Threshold**, **DS Level High Threshold**, **DS Level Low Threshold**, **DS SNR Low Threshold, DS UR High Threshold**, **US CR High Threshold**, **US CS High Threshold**, **US Level High Threshold**, **US Level Low Threshold**, **US SNR Low Threshold** and **US UR High Threshold**.

Other threshold parameters are used to determine whether or not to offload a value. With the **Minimum Variation DS SNR** and **Minimum Variation US SNR** parameters, you can make sure that there will only be a change of the parameter value if the difference between the polled value and the previous value is larger than the setting in this minimum variation parameter. The **CR Offload Threshold, CS Offload Threshold** and **UR Offload Threshold** parameter are used to ensure that there will always be an offload if the polled value is larger than or equal to the configured value.

### Configuration of the home gateway parameters

**Homestatistics Polling** enables the polling of the home gateway statistics. These statistics are polled once per day per modem. The client stats are polled between 7 p.m. and 9 p.m. in order to get the stats during the internet peak. With the parameter **Poll Clientstats 15 Min**, this polling interval can be changed, so that the client stats are then polled every 15 minutes. Polling of other statistics (channel loading, connected clients, client errors, connected power line, lan user, powerline network) is always spread over the entire day.

### Configuration of the Adlex Nouveau parameters

The CM Collector checks the current internet usage of the cable modem to determine the class to which it belongs. This info is then sent towards Adlex Nouveau in a trap. Adlex Nouveau will perform tests on modems that are not in use, in order to determine the maximum upload and download speed that can be reached. You can enable this functionality by setting the **Poll Classification** parameter to *Enabled*.

The **Trap Table** contains the IP addresses of the Adlex DMAs to which the traps can be sent. You can add IP addresses to this table by setting the parameter **Add Trap IP**. You can remove them again with the **Delete Trap IP** parameter.

The **Hardware Table** contains all the types of modems for which traps may be sent towards Adlex. You can add hardware types by setting the parameter **Add Hardware Type**, and remove them again with the **Delete Hardware Type** parameter.

The **Classification** table contains the definitions of all the classes. You can add rows to this table by clicking the **Add Class** button, and remove them again with the **Delete Class** parameter.

- **Product Type** is the internet product.
- **Flow Direction** determines if it is a classification for upstream or downstream.
- **Class** determines the class.
- **Byte Count Delta** contains the maximum delta between this polling and previous polling to suffice for this class. For example, if byte count delta class 1 is 1,000,000 and byte count delta class 2 is 5,000,000, this means that if there is a delta of 3,000,000, this will be a class 2 modem at this moment.

## Usage

As described above, the CM Collector is not intended to be used separately. The resulting data should be consulted with the CPE Manager interface of the CPE Manager elements.

## Generated CSV files

The CM Collector will generate tab-separated CSV files. For more information on the location of these files, refer to the Configuration chapter above.

### Slow offload structure

1. MAC Address 1.3.6.1.2.1.2.2.1.6.2
1. SAPID
1. Another Operator
1. Node
1. Timestamp
1. Chassis
1. HardwareVersion 1.3.6.1.2.1.1.1.0
1. ModelType 1.3.6.1.2.1.1.1.0
1. HardwareClass 1.3.6.1.2.1.1.1.0
1. DocsisType 1.3.6.1.2.1.10.127.1.1.5.0
1. SW Version 1.3.6.1.2.1.69.1.3.5.0
1. Last Change Datetime Calculated out of itf last change 1.3.6.1.2.1.2.2.1.9.1 and System Uptime 1.3.6.1.2.1.1.3.0
1. System Uptime 1.3.6.1.2.1.1.3.0
1. Downstream Maxtrafficrate 1.3.6.1.2.1.10.127.7.1.2.2.6, Docsis 2.0 from CMTS 1.3.6.1.2.1.10.127.7.1.2.2.6, Docsis 3.0 1.3.6.1.4.1.4491.2.1.21.1.2.1.6
1. Upstream MaxTrafficrate 1.3.6.1.2.1.10.127.7.1.2.2.6, Docsis 2.0 from CMTS 1.3.6.1.2.1.10.127.7.1.2.2.6, Docsis 3.0 1.3.6.1.4.1.4491.2.1.21.1.2.1.6
1. Physical Address \[Media\] 1.3.6.1.2.1.4.22.1.2
1. System Contact 1.3.6.1.2.1.1.4.0
1. Homegateway RouterMAC 1.3.6.1.2.1.2.2.1.6.1 (Motorola 2.0) or 1.3.6.1.2.1.2.2.1.6.20 (Motorola 3.0) or 1.3.6.1.2.1.2.2.1.6.20 (CBN 3.0) or 1.3.6.1.2.1.2.2.1.6.20 (UBEE 3.0)
1. Homegateway ChannelNumber 1.3.6.1.4.1.1166.1.19.51.1.5.1.2.0 (Motorola 2.0) or 1.3.6.1.4.1.1166.1.19.51.1.5.1.2.0 (Motorola 3.0) or 1.3.6.1.4.1.35604.1.19.51.1.5.1.2.0 (CBN 3.0) or 1.3.6.1.4.1.4684.54.1.1.4.1.32.1 (UBEE 3.0)
1. Homegateway ChannelWidth 1.3.6.1.4.1.1166.1.19.51.1.5.1.19.0 (Motorola 2.0) or 1.3.6.1.4.1.1166.1.19.51.1.5.1.19.0 (Motorola 3.0) or 1.3.6.1.4.1.35604.1.19.51.1.5.1.19.0 (CBN 3.0) or 1.3.6.1.4.1.4684.54.1.1.4.1.7.1 (UBEE 3.0)
1. DynamicOID1
1. DynamicOID2
1. DynamicOID3

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|MAC Address|Cable Modem MAC address|1.3.6.1.2.1.2.2.1.6.2|`ifPhysAddress.2`, MAC address of the second interface|
|2|SAPID|Service Access Point ID|N/A|N/A|
|3|Another Operator|Field used to distinguish between different operators|N/A|N/A|
|4|Node|Node to which the CM is connected|N/A|N/A|
|5|Timestamp|Time of polling|N/A|N/A|
|6|Chassis|Chassis reference|N/A|N/A|
|7|Hardware Version|Hardware version of the CM|1.3.6.1.2.1.1.1.0|`sysDescr.0`, Hardware version of the CM|
|8|Model Type|Model type of the CM|1.3.6.1.2.1.1.1.0|`sysDescr.0`, Model type of the CM|
|9|Hardware Class|Hardware class of the CM|1.3.6.1.2.1.1.1.0|`sysDescr.0`, Hardware class of the CM|
|10|DOCSIS Version|DOCSIS version of the CM|1.3.6.1.2.1.10.127.1.1.5.0|`docsIfCmStatusDocsisVersion.0`, DOCSIS version of the CM|
|11|SW Version|Software version of the CM|1.3.6.1.2.1.69.1.3.5.0|`docsIfCmSwVersion.0`, Software version of the CM|
|12|Last Change Datetime|Datetime of the last change|1.3.6.1.2.1.2.2.1.9.1, 1.3.6.1.2.1.1.3.0|`ifLastChange.1`, `sysUpTime.0`, Datetime of the last change|
|13|System Uptime|Uptime of the system|1.3.6.1.2.1.1.3.0|`sysUpTime.0`, Uptime of the system|
|14|Downstream Max Traffic Rate|Maximum downstream traffic rate (see [Downstream Max Traffic Rate](#downstream-max-traffic-rate))|N/A|N/A|
|15|Upstream Max Traffic Rate|Maximum upstream traffic rate (see [Upstream Max Traffic Rate](#upstream-max-traffic-rate))|N/A|N/A|
|16|Physical Address \[Media\]|Physical address of the media|1.3.6.1.2.1.2.2.1.6.2|`ifPhysAddress.2`, Physical address of the media|
|17|System Contact|Contact information of the system|1.3.6.1.2.1.1.4.0|`sysContact.0`, Contact information of the system|
|18|Home Gateway Router MAC|MAC address of the home gateway router (see [Home Gateway Router MAC](#home-gateway-router-mac))|N/A|N/A|
|19|Home Gateway Channel Number|Channel number of the home gateway (see [Home Gateway Channel Number](#home-gateway-channel-number))|N/A|N/A|
|20|Home Gateway Channel Width|Channel width of the home gateway (see [Home Gateway Channel Width](#home-gateway-channel-width))|N/A|N/A|
|21|DynamicOID1|Dynamic OID 1 (see [Dynamic OIDs](#dynamic-oids))|N/A|N/A|
|22|DynamicOID2|Dynamic OID 2 (see [Dynamic OIDs](#dynamic-oids))|N/A|N/A|
|23|DynamicOID3|Dynamic OID 3 (see [Dynamic OIDs](#dynamic-oids))|N/A|N/A|

#### Last Change Datetime

Calculated from the difference between the current system uptime and the last change time of the interface.

#### Downstream Max Traffic Rate

Maximum traffic rate for the downstream direction. The OID depends on the DOCSIS version of the CM and the source of the data (CM or CMTS). The table below gives an overview of the OIDs used for this parameter:

|DOCSIS Type|CM OID|CMTS OID|OID Description|
|-----------|------|--------|---------------|
|DOCSIS 1.0|1.3.6.1.2.1.10.127.7.1.2.1.6|N/A|`docsQosParamSetMaxTrafficRate`, DOCS-QOS-MIB|
|DOCSIS 2.0|N/A|1.3.6.1.2.1.10.127.7.1.2.1.6|`docsQosParamSetMaxTrafficRate`, DOCS-QOS-MIB|
|DOCSIS 3.0|1.3.6.1.4.1.4491.2.1.21.1.2.1.6|N/A|`docsQosParamSetMaxTrafficRate`, DOCS-QOS3-MIB|

#### Upstream Max Traffic Rate

Maximum traffic rate for the upstream direction. The OID depends on the DOCSIS version of the CM and the source of the data (CM or CMTS). The table below gives an overview of the OIDs used for this parameter:

|DOCSIS Type|CM OID|CMTS OID|OID Description|
|-----------|------|--------|---------------|
|DOCSIS 1.0|1.3.6.1.2.1.10.127.7.1.2.1.6|N/A|`docsQosParamSetMaxTrafficRate`, DOCS-QOS-MIB|
|DOCSIS 2.0|N/A|1.3.6.1.2.1.10.127.7.1.2.1.6|`docsQosParamSetMaxTrafficRate`, DOCS-QOS-MIB|
|DOCSIS 3.0|1.3.6.1.4.1.4491.2.1.21.1.2.1.6|N/A|`docsQosParamSetMaxTrafficRate`, DOCS-QOS3-MIB|

> [!NOTE]
> The direction of the traffic rate cannot be determined from the OID, so the same OID is used for both downstream and upstream.

#### Home Gateway Router MAC

|Vendor|OID|Description|
|------|---|-----------|
|Motorola 2.0|1.3.6.1.2.1.2.2.1.6.1|MAC address of the first interface,`ifPhysAddress.1`|
|Motorola 3.0|1.3.6.1.2.1.2.2.1.6.20|MAC address of the 20th interface,`ifPhysAddress.20`|
|CBN 3.0|1.3.6.1.2.1.2.2.1.6.20|MAC address of the 20th interface,`ifPhysAddress.20`|
|UBEE 3.0|1.3.6.1.2.1.2.2.1.6.20|MAC address of the 20th interface,`ifPhysAddress.20`|

#### Home Gateway Channel Number

|Vendor|OID|Description|
|------|---|-----------|
|Motorola 2.0|1.3.6.1.4.1.1166.1.19.51.1.5.1.2.0|Home Gateway Channel Number|
|Motorola 3.0|1.3.6.1.4.1.1166.1.19.51.1.5.1.2.0|Home Gateway Channel Number|
|CBN 3.0|1.3.6.1.4.1.35604.1.19.51.1.5.1.2.0|Home Gateway Channel Number|
|UBEE 3.0|1.3.6.1.4.1.4684.54.1.1.4.1.32.1|Home Gateway Channel Number|

#### Home Gateway Channel Width

|Vendor|OID|Description|
|------|---|-----------|
|Motorola 2.0|1.3.6.1.4.1.1166.1.19.51.1.5.1.19.0|Home Gateway Channel Width|
|Motorola 3.0|1.3.6.1.4.1.1166.1.19.51.1.5.1.19.0|Home Gateway Channel Width|
|CBN 3.0|1.3.6.1.4.1.35604.1.19.51.1.5.1.19.0|Home Gateway Channel Width|
|UBEE 3.0|1.3.6.1.4.1.4684.54.1.1.4.1.7.1|Home Gateway Channel Width|

#### Dynamic OIDs

The Dynamic OIDs are a set of parameters that can be configured in the page **Dynamic OIDs**. These parameters allow you to set custom OIDs so they can be included in the offload files. The connector supports up to 3 dynamic OIDs. Additional settings for these OIDs are the following (available per Dynamic OID):

- **Dynamic OID Description**: This is a description of the OID that will be used in the offload file. It is not mandatory to fill in this field, but it can be useful to have a clear description of the OID in the offload file.

- **Dynamic OID Offload**: If this is set to *Yes*, the value of the OID will be offloaded in the slow offload file. If it is set to *No*, the value of the OID will not be offloaded.

- **Dynamic OID Offload Cycle**: This setting determines the frequency at which the OID will be offloaded. There are two possible values: *Slow* and *Fast*. If it is set to *Slow*, the value of the OID will be offloaded in the slow offload file, which is generated once per day. If it is set to *Fast*, the value of the OID will be offloaded in the fast offload file, which is generated every 15 minutes.

- **Dynamic OID Fixed Values**: If this field is filled in, the value of the OID will be fixed to the value in this field in the slow offload file. This can be useful if the OID is not supported by all CMs, but you still want to have a value in the offload file.

- **Dynamic OID Low Range**: If the value of the OID is a number, and this field is filled in, the value of the OID will only be offloaded if it is lower than the value in this field. This can be useful to only offload values that are below a certain threshold.

- **Dynamic OID High Range**: If the value of the OID is a number, and this field is filled in, the value of the OID will only be offloaded if it is higher than the value in this field. This can be useful to only offload values that are above a certain threshold.

### Fast offload structure

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|MAC Address|Cable Modem MAC address|1.3.6.1.2.1.2.2.1.6.2|`ifPhysAddress.2`, MAC address of the second interface|
|2|SAPID|Service Access Point ID|N/A|N/A|
|3|Another Operator|Field used to distinguish between different operators|N/A|N/A|
|4|Node|Node to which the CM is connected|N/A|N/A|
|5|Timestamp|Time of polling|N/A|N/A|
|6|Chassis|Chassis reference|N/A|N/A|
|7|DynamicOID1|Dynamic OID 1 (see [Dynamic OIDs](#dynamic-oids))|N/A|N/A|
|8|DynamicOID2|Dynamic OID 2 (see [Dynamic OIDs](#dynamic-oids))|N/A|N/A|
|9|DynamicOID3|Dynamic OID 3 (see [Dynamic OIDs](#dynamic-oids))|N/A|N/A|

### Fast DS tuner offload structure

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|MAC Address|Cable Modem MAC address|1.3.6.1.2.1.2.2.1.6.2|`ifPhysAddress.2`, MAC address of the second interface|
|2|SAPID|Service Access Point ID|N/A|N/A|
|3|Another Operator|Field used to distinguish between different operators|N/A|N/A|
|4|Node|Node to which the CM is connected|N/A|N/A|
|5|Timestamp|Time of polling|N/A|N/A|
|6|Chassis|Chassis reference|N/A|N/A|
|7|Tuner ID Instance|Tuner ID instance|1.3.6.1.2.1.10.127.1.1.1.1.1|`docsIfDownChannelId`. The CMTS identification of the downstream channel|
|8|DS Frequency|Downstream frequency|1.3.6.1.2.1.10.127.1.1.1.1.2|`docsIfDownChannelFrequency`. The center of the frequency band associated with this downstream interface|
|9|DS SNR|Downstream SNR|1.3.6.1.2.1.10.127.1.1.4.1.5|`docsIfDownChannelSNR`. The signal-to-noise ratio of the downstream channel|
|10|DS Rx Power|Downstream Rx Power|1.3.6.1.2.1.10.127.1.1.1.1.6|`docsIfDownChannelPower`. The received power level of the downstream channel|
|11|DS Microreflections|Downstream Microreflections|1.3.6.1.2.1.10.127.1.1.4.1.6|`docsIfDownChannelMicroreflections`. Total microreflections including in-channel response as perceived on this interface, measured in dBc below the signal level|
|12|Modulation Type|Downstream modulation type|1.3.6.1.2.1.10.127.1.1.1.1.4|`docsIfDownChannelModulation`. The modulation type of the downstream channel|
|13|CR|Correctable Ratio (CR) (see [DS Correctable and Uncorrectable Ratios](#ds-correctable-and-uncorrectable-ratios))|N/A|N/A|
|14|UR|Uncorrectable Ratio (UR) (see [DS Correctable and Uncorrectable Ratios](#ds-correctable-and-uncorrectable-ratios))|N/A|N/A|
|15|DS Main Frequency|Primary Downstream Channel Indicator|1.3.6.1.4.1.4491.2.1.20.1.9.1.3|`docsIf3RxChStatusPrimaryDsIndicator`. If set to `true`, it indicates the Receive channel is set to be the primary-capable downstream channel for the CM receiving this RCC|

>[!NOTE]
> RCC refers to the *Receive Channel Configuration* TLV that the CMTS sents to the CM during the registration to describe the downstream channel set the CM must receive, including which channel is the primary downstream. A CM has exactly one primary DS at any time; if it loses lock on it (Lost Sync, T4), it must reinitialize the MAC.

#### DS Correctable and Uncorrectable Ratios

These ratios are calculated from the number of uncorrectable, correctable, and unerrored codewords:

|Name|SNMP OID|OID Description|
|----|--------|---------------|
|Unerroreds|1.3.6.1.2.1.10.127.1.1.4.1.2|`docsIfSigQUnerroreds`. The codewords that were received without any errors from this interface|
|Correcteds|1.3.6.1.2.1.10.127.1.1.4.1.3|`docsIfSigQCorrecteds`. The codewords that were received with correctable errors from this interface|
|Uncorrectables|1.3.6.1.2.1.10.127.1.1.4.1.4|`docsIfSigQUncorrectables`. The codewords that were received with uncorrectable errors from this interface|

$$
\text{Corrected Ratio}=\frac{\text{Correcteds}}{\text{Unerroreds}+\text{Correcteds}+\text{Uncorrectables}}\times{100}
$$

$$
\text{Uncorrected Ratio}=\frac{\text{Uncorrectables}}{\text{Unerroreds}+\text{Correcteds}+\text{Uncorrectables}}\times{1000000}
$$

1. MAC Address 1.3.6.1.2.1.2.2.1.6.2
1. SAPID
1. Another Operator
1. Node
1. Timestamp
1. Chassis
1. Tuner ID Instance of 1.3.6.1.2.1.10.127.1.1.1.1
1. DS Frequency 1.3.6.1.2.1.10.127.1.1.1.1.2
1. DS SNR 1.3.6.1.2.1.10.127.1.1.4.1.5
1. DS Rx Power 1.3.6.1.2.1.10.127.1.1.1.1.6
1. DS Microreflections 1.3.6.1.2.1.10.127.1.1.4.1.6
1. Modulation Type 1.3.6.1.2.1.10.127.1.1.1.1.4
1. CR Calculated out of Unerroreds 1.3.6.1.2.1.10.127.1.1.4.1.2, Correcteds 1.3.6.1.2.1.10.127.1.1.4.1.3, Uncorrectables 1.3.6.1.2.1.10.127.1.1.4.1.4
1. UR Calculated out of Unerroreds 1.3.6.1.2.1.10.127.1.1.4.1.2, Correcteds 1.3.6.1.2.1.10.127.1.1.4.1.3, Uncorrectables 1.3.6.1.2.1.10.127.1.1.4.1.4
1. DS Main Frequency 1.3.6.1.4.1.4491.2.1.20.1.9.1.3

### Fast US tuner offload structure

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|MAC Address|Cable Modem MAC address|1.3.6.1.2.1.2.2.1.6.2|`ifPhysAddress.2`, MAC address of the second interface|
|2|SAPID|Service Access Point ID|N/A|N/A|
|3|Another Operator|Field used to distinguish between different operators|N/A|N/A|
|4|Node|Node to which the CM is connected|N/A|N/A|
|5|Timestamp|Time of polling|N/A|N/A|
|6|Chassis|Chassis reference|N/A|N/A|
|7|Tuner ID Instance|Tuner ID instance|1.3.6.1.2.1.10.127.1.1.2.1.1|`docsIfUpChannelId`. The CMTS identification of the upstream channel|
|8|US Frequency|Upstream frequency|1.3.6.1.2.1.10.127.1.1.2.1.2|`docsIfUpChannelFrequency`. The center of the frequency band associated with this upstream interface|
|9|US Channel Width|Upstream channel width|1.3.6.1.2.1.10.127.1.1.2.1.3|`docsIfUpChannelWidth`. The bandwidth of the upstream interface|
|10|US Channel Modulation|Upstream channel modulation type|1.3.6.1.2.1.10.127.1.1.2.1.15|`docsIfUpChannelType`. The upstream channel type|
|11|US Tx Power|Upstream transmit power|See [Upstream Transmit Power](#upstream-transmit-power)|N/A|
|12|US SNR|Upstream SNR|1.3.6.1.4.1.4491.2.1.20.1.4.1.4| `docsIf3CmtsCmUsStatusSignalNoise`. The signal-to-noise ratio of the upstream channel (polled from the CMTS)|
|13|Correctable Ratio (CR)|See [US Correctable and Uncorrectable Ratios](#us-correctable-and-uncorrectable-ratios). Polled from the CMTS|N/A|N/A|
|14|Uncorrectable Ratio (UR)|See [US Correctable and Uncorrectable Ratios](#us-correctable-and-uncorrectable-ratios). Polled from the CMTS|N/A|N/A|
|15|Status Resets|Status Resets|1.3.6.1.4.1.4491.2.1.20.1.1.1.3|`docsIf3CmStatusResets`. The number of times the cable modem has reset or initializes this interface|
|16|Lost Syncs|Lost Syncs|1.3.6.1.4.1.4491.2.1.20.1.1.1.4|`docsIf3CmStatusLostSyncs`. The number of times the cable modem has lost synchronization on the downstream channel|
|17|T1 timeouts|T1 timeouts|1.3.6.1.4.1.4491.2.1.20.1.1.1.9|`docsIf3CmStatusT1Timeouts`. The number of times counter T1 expired in the CM|
|18|T2 timeouts|T2 timeouts|1.3.6.1.4.1.4491.2.1.20.1.1.1.10|`docsIf3CmStatusT2Timeouts`. The number of times counter T2 expired in the CM|
|19|T3 timeouts|T3 timeouts|1.3.6.1.4.1.4491.2.1.20.1.2.1.2|`docsIf3CmStatusUsT3Timeouts`. The number of times counter T3 expired in the CM for this upstream channel|
|20|T4 timeouts|T4 timeouts|1.3.6.1.4.1.4491.2.1.20.1.2.1.3|`docsIf3CmStatusUsT4Timeouts`. The number of times counter T4 expired in the CM for this upstream channel|
|21|Rangings aborted|Rangings aborted|1.3.6.1.4.1.4491.2.1.20.1.2.1.4|`docsIf3CmStatusUsRangingsAborted`. The number of times the ranging process was aborted by the CMTS|

#### Upstream Transmit Power

|DOCSIS Type|CM OID|CMTS OID|OID Description|
|-----------|------|--------|---------------|
|Default|1.3.6.1.4.1.4491.2.1.20.1.2.1.1|N/A|`docsIf3CmStatusUsTxPower`. The operational transmit CM transmit power for this SC-QAM upstream channel.|
|DOCSIS 2.0|1.3.6.1.2.1.10.127.1.2.2.1.3.2|N/A|`docsIfCmStatusTxPower`. The operational transmit power of the upstream channel|

#### US Correctable and Uncorrectable Ratios

These ratios are calculated from the number of uncorrectable, correctable, and unerrored codewords:

|Name|SNMP OID|OID Description|
|----|--------|---------------|
|Unerroreds|1.3.6.1.4.1.4491.2.1.20.1.4.1.7|`docsIf3CmtsCmUsStatusUnerroreds`. The codewords that were received without any errors from this interface|
|Correcteds|1.3.6.1.4.1.4491.2.1.20.1.4.1.8|`docsIf3CmtsCmUsStatusCorrecteds`. The codewords that were received with correctable errors from this interface|
|Uncorrectables|1.3.6.1.4.1.4491.2.1.20.1.4.1.9|`docsIf3CmtsCmUsStatusUncorrectables`. The codewords that were received with uncorrectable errors from this interface|

$$
\text{Corrected Ratio}=\frac{\text{Correcteds}}{\text{Unerroreds}+\text{Correcteds}+\text{Uncorrectables}}\times{100}
$$

$$
\text{Uncorrected Ratio}=\frac{\text{Uncorrectables}}{\text{Unerroreds}+\text{Correcteds}+\text{Uncorrectables}}\times{1000000}
$$

1. MAC Address 1.3.6.1.2.1.2.2.1.6.2
1. SAPID
1. Another Operator
1. Node
1. Timestamp
1. Chassis
1. Tuner ID 1.3.6.1.2.1.10.127.1.1.2.1.1
1. US Frequency 1.3.6.1.2.1.10.127.1.1.2.1.2
1. US Channel Width 1.3.6.1.2.1.10.127.1.1.2.1.3
1. US Channel Modulation 1.3.6.1.2.1.10.127.1.1.2.1.15
1. US Tx 1.3.6.1.4.1.4491.2.1.20.1.2.1.1 or 1.3.6.1.2.1.10.127.1.2.2.1.3.2 (Docsis 2.0)
1. US SNR Polled from CMTS 1.3.6.1.4.1.4491.2.1.20.1.4.1.4
1. CR Polled from CMTS, calculated out of Unerroreds 1.3.6.1.4.1.4491.2.1.20.1.4.1.7, Correcteds 1.3.6.1.4.1.4491.2.1.20.1.4.1.8, Uncorrectables 1.3.6.1.4.1.4491.2.1.20.1.4.1.9
1. UR Polled from CMTS, calculated out of Unerroreds 1.3.6.1.4.1.4491.2.1.20.1.4.1.7, Correcteds 1.3.6.1.4.1.4491.2.1.20.1.4.1.8, Uncorrectables 1.3.6.1.4.1.4491.2.1.20.1.4.1.9
1. CS Calculated out of Status Resets 1.3.6.1.4.1.4491.2.1.20.1.1.1.3, Lost Syncs 1.3.6.1.4.1.4491.2.1.20.1.1.1.4, T1 timeouts 1.3.6.1.4.1.4491.2.1.20.1.1.1.9, T2 timeouts 1.3.6.1.4.1.4491.2.1.20.1.1.1.10, T3 timeouts 1.3.6.1.4.1.4491.2.1.20.1.2.1.2, T4 timeouts 1.3.6.1.4.1.4491.2.1.20.1.2.1.3, Rangings aborted 1.3.6.1.4.1.4491.2.1.20.1.2.1.4

### IVR offload structure

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|MAC Address|Cable Modem MAC address|N/A|N/A|
|2|State|State of the cable modem|N/A|N/A|
|3|Timestamp|Time of polling|N/A|N/A|
|4|SAPID|Service Access Point ID|N/A|N/A|
|5|Another Operator|Field used to distinguish between different operators|N/A|N/A|

1. MAC Address
1. State
1. Timestamp
1. SAPID
1. Another Operator

### Clientstats offload structure

1. SAPID
1. Timestamp
1. MAC Address CM
1. 2.4 G or 5 G
1. BSS
1. MAC Address Client 1.3.6.1.4.1.35604.1.19.51.5.1.1.2 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.2.1.2 (5G)
1. RSSI 1.3.6.1.4.1.35604.1.19.51.5.1.1.5 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.2.1.5 (5G)
1. Tx 1.3.6.1.4.1.35604.1.19.51.5.1.1.6 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.2.1.6 (5G)
1. Rx 1.3.6.1.4.1.35604.1.19.51.5.1.1.7 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.2.1.7 (5G)
1. Mode 1.3.6.1.4.1.35604.1.19.51.5.1.1.8 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.2.1.8 (5G)
1. Authentication 1.3.6.1.4.1.35604.1.19.51.5.1.1.9 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.2.1.9 (5G)
1. Encryption 1.3.6.1.4.1.35604.1.19.51.5.1.1.10 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.2.1.10 (5G)
1. Another Operator

### Channeloading offload structure

1. SAPID
1. Timestamp
1. Mac Address CM
1. 2.4 G or 5 G
1. Channel Nr
1. Channel Loading 1.3.6.1.4.1.35604.1.19.51.1.7.1.1.2 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.3.3.1.1.2 (5G)
1. Channel AP Count 1.3.6.1.4.1.35604.1.19.51.1.7.1.1.3 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.3.3.1.1.3 (5G)
1. Another Operator

### Connectedclients offload structure

1. SAPID
1. Timestamp
1. MAC Address CM
1. 2.4 G or 5 G
1. BSS
1. Time Interval 1.3.6.1.4.1.35604.1.19.51.5.3.1.3 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.4.1.3 (5G)
1. Connected Clients 1.3.6.1.4.1.35604.1.19.51.5.3.1.4 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.4.1.4 (5G)
1. Max Simultaneous Clients 1.3.6.1.4.1.35604.1.19.51.5.3.1.5 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.4.1.5 (5G)
1. Max Simul Clients Timestamp 1.3.6.1.4.1.35604.1.19.51.5.3.1.6 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.4.1.6 (5G)
1. Rejected Clients 1.3.6.1.4.1.35604.1.19.51.5.3.1.7 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.4.1.7 (5G)
1. Another Operator

### Clienterrors offload structure

1. SAPID
1. Timestamp
1. MAC Address CM
1. 2.4 G or 5 G
1. BSS
1. Error Type
1. Rejected Clients 1.3.6.1.4.1.35604.1.19.51.5.5.2.1.2 (2,4G) or 1.3.6.1.4.1.35604.1.19.51.5.6.2.1.2 (5G)
1. Another Operator

### Connectedpowerline offload structure

1. SAPID
1. Timestamp
1. MAC Address CM
1. MAC Address Powerline 1.3.6.1.4.1.35604.1.19.62.1.1.6.1.2
1. Location 1.3.6.1.4.1.35604.1.19.62.1.1.6.1.3
1. Vendor 1.3.6.1.4.1.35604.1.19.62.1.1.6.1.4
1. Firmware 1.3.6.1.4.1.35604.1.19.62.1.1.6.1.5
1. Chipset 1.3.6.1.4.1.35604.1.19.62.1.1.6.1.6
1. Tx 1.3.6.1.4.1.35604.1.19.62.1.1.6.1.10
1. Rx 1.3.6.1.4.1.35604.1.19.62.1.1.6.1.11
1. Another Operator
1. n CPE Client 1.n Mac 1.3.6.1.4.1.35604.1.19.62.1.1.7.1.2

### Lanuser offload structure

1. SAPID
1. Timestamp
1. MAC Address CM
1. MAC Address LAN 1.3.6.1.4.1.35604.1.19.201.1.1.1.3
1. LAN Interface 1.3.6.1.4.1.35604.1.19.201.1.1.1.4
1. Another Operator

### Powerlinenetwork offload structure

1. SAPID
1. Timestamp
1. MAC Address CM
1. Polling Interval 1.3.6.1.4.1.35604.1.19.62.1.1.2.0
1. HPAV Network 1.3.6.1.4.1.35604.1.19.62.1.1.4.0
1. HPAV CCO 1.3.6.1.4.1.35604.1.19.62.1.1.5.0
1. Another Operator
