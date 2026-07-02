---
uid: Connector_help_Telenet_CM_Collector
---

# Telenet CM Collector

## About

The **Telenet CM Collector** is part of the EPM Solution deployed at Telenet and works together with the **Telenet CPE Manager**, **Telenet STB Collector**, and **Telenet eMTA Collector** connectors. This connector is responsible for polling cable modems.

This connector will poll all the CMs in two poll cycles:

- **Fast Poll**: Polling CMs over a 15-minute period.
- **Slow Poll**: Polling CMs over a 24-hour period.

In addition, there is another poll cycle that polls the **CMTS** to request the US data of all CMs over a 15-minute period. The polled data is offloaded into CSV files and aggregated by the CPE Manager element. The CPE Manager element provisions the CM Collector with the CMs that need to be polled and their IP addresses. The CM Collector sends traps to *Adlex Nouveau*.

## Configuration

### Connections

This connector uses two Simple Network Management Protocol (SNMP) connections. The first SNMP connection is used to connect to the CM and the second one to connect to the CMTS.

The following input is required during element creation:

**SNMP Connection:**

- **IP address/host**: 127.0.0.1 (IP addresses will be dynamically set by the connector when polling a specific cable modem).
- **Device address**: Not required.

**SNMP Settings:**

- **Port Number**: The port of the connected device, by default *161*.
- **Get Community String**: The community string used when reading values from the device, by default *public*.
- **Set Community String**: Not required, because the connector will not perform sets.

> [!NOTE]
> All polled CMs share the same settings, and all polled CMTS devices share the same settings.

### Offload Parameters

By default, the CM collector hide the display pages. Configuration parameters are available through:

- A Visio file assigned ot the CM Collector element.
- Multiple set operations on the CM Collector element (see [Setting a parameter value in multiple elements](https://docs.dataminer.services/dataminer/Operator_guide/Elements/Working_with_elements/Updating_elements.html#setting-a-parameter-value-in-multiple-elements)).

> [!NOTE]
> When creating a CM Collector element, a Visio will automatically be assigned to the element.

The following parameters can be configured:

- **Data Offload Folder**: Location of the fast and slow offload files. Default value is *D:\ConfiguratieData\Offload\Modem_Info*.

- **RCCV Data Offload Folder**: Location of the IVR files. Default value is *D:\ConfiguratieData\Offload\rccv_info*.

Certain offload paths are hardcoded in the CM Collector:

- **HGW Data Offload Folder**: Location of the HGW files. Default value is *D:\ConfiguratieData\Offload\HGW*.

### Threshold Parameters

The threshold parameters are used during aggregation. If the parameter in the CPE Manager is `%CM With DS SNR < T`, then the DS SNR parameter is compared with the **DS SNR Low Threshold**. If the SNR is below the value in the configuration parameter, then the CM is taken into account for the aggregation. The same applies for the other threshold parameters.

The following parameters can be configured:

- DS CR High Threshold
- DS CS High Threshold
- DS Level High Threshold
- DS Level Low Threshold
- DS SNR Low Threshold
- DS UR High Threshold
- US CR High Threshold
- US CS High Threshold
- US Level High Threshold
- US Level Low Threshold
- US SNR Low Threshold
- US UR High Threshold

Other threshold parameters are used to determine whether or not to offload a value. With the **Minimum Variation DS SNR** and **Minimum Variation US SNR** parameters, you can make sure that there will only be a change of the parameter value if the difference between the polled value and the previous value is larger than the setting in this minimum variation parameter. The **CR Offload Threshold**, **CS Offload Threshold**, and **UR Offload Threshold** parameters are used to ensure that there will always be an offload if the polled value is larger than or equal to the configured value.

### Home Gateway Parameters

**Homestatistics Polling** enables the polling of the home gateway statistics. These statistics are polled once per day per modem. The client stats are polled between 7 p.m. and 9 p.m. in order to get the stats during the internet peak. With the parameter **Poll Clientstats 15 Min**, this polling interval can be changed, so that the client stats are then polled every 15 minutes. Polling of other statistics (channel loading, connected clients, client errors, connected power line, LAN user, powerline network) is always spread over the entire day.

### Adlex Nouveau Parameters

The CM Collector checks the current internet usage of the cable modem to determine the class to which it belongs. This information is then sent to *Adlex Nouveau* in a trap. *Adlex Nouveau* will perform tests on modems that are not in use, in order to determine the maximum upload and download speed that can be reached. You can enable this functionality by setting the **Poll Classification** parameter to *Enabled*.

The **Trap Table** contains the IP addresses of the Adlex DMAs to which the traps can be sent. You can add IP addresses to this table by setting the parameter **Add Trap IP**. You can remove them again with the **Delete Trap IP** parameter.

The **Hardware Table** contains all the types of modems for which traps may be sent to *Adlex Nouveau*. You can add hardware types by setting the parameter **Add Hardware Type**, and remove them again with the **Delete Hardware Type** parameter.

The **Classification** table contains the definitions of all the classes. You can add rows to this table by clicking the **Add Class** button, and remove them again with the **Delete Class** parameter.

- **Product Type** is the internet product.
- **Flow Direction** determines if it is a classification for upstream or downstream.
- **Class** determines the class.
- **Byte Count Delta** contains the maximum delta between this polling and previous polling to suffice for this class. For example, if byte count delta class 1 is 1,000,000 and byte count delta class 2 is 5,000,000, this means that if there is a delta of 3,000,000, this will be a class 2 modem at this moment.

## Usage

As described above, the CM Collector is not intended to be used separately. The resulting data should be consulted in the CPE Manager interface of the CPE Manager elements.

## Generated Offload Files

- The CM Collector will generate offload files including information from the monitored cable modems and relevant information about the infrastructure that provides services to the cable modems. For more information on the location of these files, refer to [Offload Parameters](#offload-parameters).
- There will be a CSV file generated per operator.

### Slow Offload Structure

- Offload format: Tab-separated CSV file
- Offload folder: **HGW Data Offload Folder**
- Offload file structure: `<DMAID>_<EID>_CMS.ClientStats.<OPERATOR>.current.csv`
  - DMAID: DMA ID where the CM collector element is located.
  - EID: Element ID of the CM collector element.
  - OPERATOR: Operator assigned to the CMs available if the offload file.

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|MAC Address|Cable Modem MAC address|1.3.6.1.2.1.2.2.1.6.2|`ifPhysAddress.2`, MAC address of the second interface|
|2|SAPID|Service Access Point ID|N/A|N/A|
|3|Another Operator|Field used to distinguish between different operators|N/A|N/A|
|4|Node|Node to which the CM is connected|N/A|N/A|
|5|Timestamp|Time of polling|N/A|N/A|
|6|Chassis|Chassis reference|N/A|N/A|
|7|Hardware Version|Hardware version of the CM|1.3.6.1.2.1.1.1.0|`sysDescr.0`, hardware version of the CM|
|8|Model Type|Model type of the CM|1.3.6.1.2.1.1.1.0|`sysDescr.0`, model type of the CM|
|9|Hardware Class|Hardware class of the CM|1.3.6.1.2.1.1.1.0|`sysDescr.0`, hardware class of the CM|
|10|DOCSIS Version|DOCSIS version of the CM|1.3.6.1.2.1.10.127.1.1.5.0|`docsIfCmStatusDocsisVersion.0`, DOCSIS version of the CM|
|11|SW Version|Software version of the CM|1.3.6.1.2.1.69.1.3.5.0|`docsIfCmSwVersion.0`, software version of the CM|
|12|Last Change Datetime|Datetime of the last change|1.3.6.1.2.1.2.2.1.9.1, 1.3.6.1.2.1.1.3.0|`ifLastChange.1`, `sysUpTime.0`, datetime of the last change|
|13|System Uptime|Uptime of the system|1.3.6.1.2.1.1.3.0|`sysUpTime.0`, uptime of the system|
|14|Downstream Max Traffic Rate|Maximum downstream traffic rate (see [Downstream Max Traffic Rate](#downstream-max-traffic-rate))|N/A|N/A|
|15|Upstream Max Traffic Rate|Maximum upstream traffic rate (see [Upstream Max Traffic Rate](#upstream-max-traffic-rate))|N/A|N/A|
|16|Physical Address \[Media\]|Physical address of the media|1.3.6.1.2.1.2.2.1.6.2|`ifPhysAddress.2`, physical address of the media|
|17|System Contact|Contact information of the system|1.3.6.1.2.1.1.4.0|`sysContact.0`, contact information of the system|
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

The Dynamic OIDs are a set of parameters that can be configured on the page **Dynamic OIDs**. These parameters allow you to set custom OIDs so they can be included in the offload files. The connector supports up to 3 dynamic OIDs. The following additional settings are available for each dynamic OID:

- **Dynamic OID Description**: Description of the OID that will be used in the offload file. While filling in this field is not mandatory, it can be useful to have a clear description of the OID in the offload file.

- **Dynamic OID Offload**: If this is set to *Yes*, the value of the OID will be offloaded in the slow offload file. If it is set to *No*, the value of the OID will not be offloaded.

- **Dynamic OID Offload Cycle**: Determines the frequency at which the OID will be offloaded. There are two possible values: *Slow* and *Fast*. If it is set to *Slow*, the value of the OID will be offloaded in the slow offload file, which is generated once per day. If it is set to *Fast*, the value of the OID will be offloaded in the fast offload file, which is generated every 15 minutes.

- **Dynamic OID Fixed Values**: If this field is filled in, the value of the OID will be fixed to the value in this field in the slow offload file. This can be useful if the OID is not supported by all CMs, but you still want to have a value in the offload file.

- **Dynamic OID Low Range**: If the value of the OID is a number, and this field is filled in, the value of the OID will only be offloaded if it is lower than the value in this field. This can be useful to only offload values that are below a certain threshold.

- **Dynamic OID High Range**: If the value of the OID is a number, and this field is filled in, the value of the OID will only be offloaded if it is higher than the value in this field. This can be useful to only offload values that are above a certain threshold.

### Fast Offload Structure

- Offload format: Tab-separated CSV file
- Offload folder: **Data Offload Folder**
- Offload file structure: `<DMAID>_<EID>_CMS.fast.dataoffload.<OPERATOR>.current.csv`
  - DMAID: DMA ID where the CM collector element is located.
  - EID: Element ID of the CM collector element.
  - OPERATOR: Operator assigned to the CMs available if the offload file.

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
|10|Partial Service State|Partial service state of the CM|1.3.6.1.4.1.4491.2.1.28.1.3.1.9|`docsIf31CmtsCmRegStatusPartialSvcState`. Type of *bondingGroup* issue that the CM experiences|
|11|Partial Channel State|Partial channel state of the CM|1.3.6.1.4.1.4491.2.1.28.1.3.1.10|`docsIf31CmtsCmRegStatusPartialChanState`. Type of OFDM *channel* issue that the CM experiences|

> [!NOTE]
> **Partial service state** and **Partial channel state** are only available for DOCSIS 3.1 CMs. For DOCSIS 3.0 and lower, these fields will be empty.

### Fast DS Tuner Offload Structure

- Offload format: Tab-separated CSV file
- Offload folder: **Data Offload Folder**
- Offload file structure: `<DMAID>.<EID>.DS.Tuner.<OPERATOR>.current.csv`
  - DMAID: DMA ID where the CM collector element is located.
  - EID: Element ID of the CM collector element.
  - OPERATOR: Operator assigned to the CMs available if the offload file.

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|MAC Address|Cable Modem MAC address|1.3.6.1.2.1.2.2.1.6.2|`ifPhysAddress.2`, MAC address of the second interface|
|2|SAPID|Service Access Point ID|N/A|N/A|
|3|Another Operator|Field used to distinguish between different operators|N/A|N/A|
|4|Node|Node to which the CM is connected|N/A|N/A|
|5|Timestamp|Time of polling|N/A|N/A|
|6|Chassis|Chassis reference|N/A|N/A|
|7|Tuner ID Instance|Tuner ID instance|1.3.6.1.2.1.10.127.1.1.1.1.1|`docsIfDownChannelId`, the CMTS identification of the downstream channel|
|8|DS Frequency|Downstream frequency|1.3.6.1.2.1.10.127.1.1.1.1.2|`docsIfDownChannelFrequency`, the center of the frequency band associated with this downstream interface|
|9|DS SNR|Downstream SNR|1.3.6.1.2.1.10.127.1.1.4.1.5|`docsIfDownChannelSNR`, the signal-to-noise ratio of the downstream channel|
|10|DS Rx Power|Downstream Rx Power|1.3.6.1.2.1.10.127.1.1.1.1.6|`docsIfDownChannelPower`, the received power level of the downstream channel|
|11|DS Microreflections|Downstream Microreflections|1.3.6.1.2.1.10.127.1.1.4.1.6|`docsIfDownChannelMicroreflections`, the total microreflections including in-channel response as perceived on this interface, measured in dBc below the signal level|
|12|Modulation Type|Downstream modulation type|1.3.6.1.2.1.10.127.1.1.1.1.4|`docsIfDownChannelModulation`, the modulation type of the downstream channel|
|13|CR|Correctable Ratio (CR) (see [DS Correctable and Uncorrectable Ratios](#ds-correctable-and-uncorrectable-ratios))|N/A|N/A|
|14|UR|Uncorrectable Ratio (UR) (see [DS Correctable and Uncorrectable Ratios](#ds-correctable-and-uncorrectable-ratios))|N/A|N/A|
|15|DS Main Frequency|Primary Downstream Channel Indicator|1.3.6.1.4.1.4491.2.1.20.1.9.1.3|`docsIf3RxChStatusPrimaryDsIndicator`. If set to `true`, this indicates that the Receive channel is set to be the primary-capable downstream channel for the CM receiving this RCC.|

> [!NOTE]
> RCC refers to the **Receive Channel Configuration** TLV that the CMTS sends to the CM during the registration to describe the downstream channel set the CM must receive, including which channel is the primary downstream. A CM has exactly one primary DS at any time; if it loses lock on it (Lost Sync, T4), it must reinitialize the MAC.

#### DS Correctable and Uncorrectable Ratios

These ratios are calculated from the number of uncorrectable, correctable, and unerrored codewords:

|Name|SNMP OID|OID Description|
|----|--------|---------------|
|Unerroreds|1.3.6.1.2.1.10.127.1.1.4.1.2|`docsIfSigQUnerroreds`, the codewords that were received without any errors from this interface|
|Correcteds|1.3.6.1.2.1.10.127.1.1.4.1.3|`docsIfSigQCorrecteds`, the codewords that were received with correctable errors from this interface|
|Uncorrectables|1.3.6.1.2.1.10.127.1.1.4.1.4|`docsIfSigQUncorrectables`, the codewords that were received with uncorrectable errors from this interface|

$$
\text{Corrected Ratio}=\frac{\text{Correcteds}}{\text{Unerroreds}+\text{Correcteds}+\text{Uncorrectables}}\times{100}
$$

$$
\text{Uncorrected Ratio}=\frac{\text{Uncorrectables}}{\text{Unerroreds}+\text{Correcteds}+\text{Uncorrectables}}\times{1000000}
$$

### Fast US Tuner Offload Structure

- Offload format: Tab-separated CSV file
- Offload folder: **Data Offload Folder**
- Offload file structure: `<DMAID>.<EID>.US.Tuner.<OPERATOR>.current.csv`
  - DMAID: DMA ID where the CM collector element is located.
  - EID: Element ID of the CM collector element.
  - OPERATOR: Operator assigned to the CMs available if the offload file.

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|MAC Address|Cable Modem MAC address|1.3.6.1.2.1.2.2.1.6.2|`ifPhysAddress.2`, MAC address of the second interface|
|2|SAPID|Service Access Point ID|N/A|N/A|
|3|Another Operator|Field used to distinguish between different operators|N/A|N/A|
|4|Node|Node to which the CM is connected|N/A|N/A|
|5|Timestamp|Time of polling|N/A|N/A|
|6|Chassis|Chassis reference|N/A|N/A|
|7|Tuner ID Instance|Tuner ID instance|1.3.6.1.2.1.10.127.1.1.2.1.1|`docsIfUpChannelId`, the CMTS identification of the upstream channel|
|8|US Frequency|Upstream frequency|1.3.6.1.2.1.10.127.1.1.2.1.2|`docsIfUpChannelFrequency`, the center of the frequency band associated with this upstream interface|
|9|US Channel Width|Upstream channel width|1.3.6.1.2.1.10.127.1.1.2.1.3|`docsIfUpChannelWidth`, the bandwidth of the upstream interface|
|10|US Channel Modulation|Upstream channel modulation type|1.3.6.1.2.1.10.127.1.1.2.1.15|`docsIfUpChannelType`, the upstream channel type|
|11|US Tx Power|Upstream transmit power|See [Upstream Transmit Power](#upstream-transmit-power)|N/A|
|12|US SNR|Upstream SNR|1.3.6.1.4.1.4491.2.1.20.1.4.1.4| `docsIf3CmtsCmUsStatusSignalNoise`, the signal-to-noise ratio of the upstream channel (polled from the CMTS)|
|13|Correctable Ratio (CR)|See [US Correctable and Uncorrectable Ratios](#us-correctable-and-uncorrectable-ratios). Polled from the CMTS|N/A|N/A|
|14|Uncorrectable Ratio (UR)|See [US Correctable and Uncorrectable Ratios](#us-correctable-and-uncorrectable-ratios). Polled from the CMTS|N/A|N/A|
|15|Status Resets|Status Resets|1.3.6.1.4.1.4491.2.1.20.1.1.1.3|`docsIf3CmStatusResets`, the number of times the cable modem has reset or initialized this interface|
|16|Lost Syncs|Lost Syncs|1.3.6.1.4.1.4491.2.1.20.1.1.1.4|`docsIf3CmStatusLostSyncs`, the number of times the cable modem has lost synchronization on the downstream channel|
|17|T1 timeouts|T1 timeouts|1.3.6.1.4.1.4491.2.1.20.1.1.1.9|`docsIf3CmStatusT1Timeouts`, the number of times counter T1 expired in the CM|
|18|T2 timeouts|T2 timeouts|1.3.6.1.4.1.4491.2.1.20.1.1.1.10|`docsIf3CmStatusT2Timeouts`, the number of times counter T2 expired in the CM|
|19|T3 timeouts|T3 timeouts|1.3.6.1.4.1.4491.2.1.20.1.2.1.2|`docsIf3CmStatusUsT3Timeouts`, the number of times counter T3 expired in the CM for this upstream channel|
|20|T4 timeouts|T4 timeouts|1.3.6.1.4.1.4491.2.1.20.1.2.1.3|`docsIf3CmStatusUsT4Timeouts`, the number of times counter T4 expired in the CM for this upstream channel|
|21|Rangings aborted|Rangings aborted|1.3.6.1.4.1.4491.2.1.20.1.2.1.4|`docsIf3CmStatusUsRangingsAborted`, the number of times the ranging process was aborted by the CMTS|

#### Upstream Transmit Power

|DOCSIS Type|CM OID|CMTS OID|OID Description|
|-----------|------|--------|---------------|
|Default|1.3.6.1.4.1.4491.2.1.20.1.2.1.1|N/A|`docsIf3CmStatusUsTxPower`, the operational transmit CM transmit power for this SC-QAM upstream channel|
|DOCSIS 2.0|1.3.6.1.2.1.10.127.1.2.2.1.3.2|N/A|`docsIfCmStatusTxPower`, the operational transmit power of the upstream channel|

#### US Correctable and Uncorrectable Ratios

These ratios are calculated from the number of uncorrectable, correctable, and unerrored codewords:

|Name|SNMP OID|OID Description|
|----|--------|---------------|
|Unerroreds|1.3.6.1.4.1.4491.2.1.20.1.4.1.7|`docsIf3CmtsCmUsStatusUnerroreds`, the codewords that were received without any errors from this interface|
|Correcteds|1.3.6.1.4.1.4491.2.1.20.1.4.1.8|`docsIf3CmtsCmUsStatusCorrecteds`, the codewords that were received with correctable errors from this interface|
|Uncorrectables|1.3.6.1.4.1.4491.2.1.20.1.4.1.9|`docsIf3CmtsCmUsStatusUncorrectables`, the codewords that were received with uncorrectable errors from this interface|

$$
\text{Corrected Ratio}=\frac{\text{Correcteds}}{\text{Unerroreds}+\text{Correcteds}+\text{Uncorrectables}}\times{100}
$$

$$
\text{Uncorrected Ratio}=\frac{\text{Uncorrectables}}{\text{Unerroreds}+\text{Correcteds}+\text{Uncorrectables}}\times{1000000}
$$

### IVR Offload Structure

- Offload format: Binary format (DAT extension).
- Offload folder: **RCCV Data Offload Folder**
- Offload file structure: `ivr.cm.offload.<DMAID>_<EID>.<OPERATOR>.current.dat`
  - DMAID: DMA ID where the CM collector element is located.
  - EID: Element ID of the CM collector element.
  - OPERATOR: Operator assigned to the CMs available if the offload file.

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|MAC Address|Cable Modem MAC address|N/A|N/A|
|2|State|State of the cable modem|N/A|N/A|
|3|Timestamp|Time of polling|N/A|N/A|
|4|SAPID|Service Access Point ID|N/A|N/A|
|5|Another Operator|Field used to distinguish between different operators|N/A|N/A|

### Client Stats Offload Structure

- Offload format: Tab-separated CSV file
- Offload folder: **HGW Data Offload Folder**
- Offload file structure: `<DMAID>.<EID>.CMS.ClientStats.<OPERATOR>.current.csv`
  - DMAID: DMA ID where the CM collector element is located.
  - EID: Element ID of the CM collector element.
  - OPERATOR: Operator assigned to the CMs available if the offload file.

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|SAPID|Service Access Point ID|N/A|N/A|
|2|Timestamp|Time of polling|N/A|N/A|
|3|MAC Address CM|Cable Modem MAC address|N/A|N/A|
|4|Frequency Access Point|Possible values: 2.4G or 5G|N/A|N/A|
|5|BSS|Basic Service Set of the connected client|N/A|N/A|
|6|MAC Address Client|See [MAC Address Client](#mac-address-client)|N/A|N/A|
|7|RSSI|See [RSSI (Received Signal Strength Indicator)](#rssi-received-signal-strength-indicator)|N/A|N/A|
|8|Tx|See [Transmit (Tx)](#transmit-tx)|N/A|N/A|
|9|Rx|See [Receive (Rx)](#receive-rx)|N/A|N/A|
|10|Mode|See [Mode](#mode)|N/A|N/A|
|11|Authentication|See [Authentication](#authentication)|N/A|N/A|
|12|Encryption|See [Encryption](#encryption)|N/A|N/A|
|13|Another Operator|Field used to distinguish between different operators|N/A|N/A|

#### MAC Address Client

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.1.1.2|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.2.1.2|N/A|

#### RSSI (Received Signal Strength Indicator)

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.1.1.5|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.2.1.5|N/A|

#### Transmit (Tx)

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.1.1.6|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.2.1.6|N/A|

#### Receive (Rx)

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.1.1.7|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.2.1.7|N/A|

#### Mode

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.1.1.8|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.2.1.8|N/A|

#### Authentication

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.1.1.9|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.2.1.9|N/A|

#### Encryption

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.1.1.10|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.2.1.10|N/A|

### Channel Loading Offload Structure

- Offload format: Tab-separated CSV file
- Offload folder: **HGW Data Offload Folder**
- Offload file structure: `<DMAID>.<EID>.CMS.ChannelLoading.<OPERATOR>.current.csv`
  - DMAID: DMA ID where the CM collector element is located.
  - EID: Element ID of the CM collector element.
  - OPERATOR: Operator assigned to the CMs available if the offload file.

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|SAPID|Service Access Point ID|N/A|N/A|
|2|Timestamp|Time of polling|N/A|N/A|
|3|MAC Address CM|Cable Modem MAC address|N/A|N/A|
|4|Frequency Access Point|Possible values: 2.4G or 5G|N/A|N/A|
|5|Channel Nr|Channel number|N/A|N/A|
|6|Channel Loading|See [Channel Loading](#channel-loading)|N/A|N/A|
|7|Channel AP Count|See [Channel AP Count](#channel-ap-count)|N/A|N/A|
|8|Another Operator|Field used to distinguish between different operators|N/A|N/A|

#### Channel Loading

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.1.7.1.1.2|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.3.3.1.1.2|N/A|

#### Channel AP Count

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.1.7.1.1.3|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.3.3.1.1.3|N/A|

### Connected Clients Offload Structure

- Offload format: Tab-separated CSV file
- Offload folder: **HGW Data Offload Folder**
- Offload file structure: `<DMAID>.<EID>.CMS.ConnectedClients.<OPERATOR>.current.csv`
  - DMAID: DMA ID where the CM collector element is located.
  - EID: Element ID of the CM collector element.
  - OPERATOR: Operator assigned to the CMs available if the offload file.

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|SAPID|Service Access Point ID|N/A|N/A|
|2|Timestamp|Time of polling|N/A|N/A|
|3|MAC Address CM|Cable Modem MAC address|N/A|N/A|
|4|Frequency Access Point|Possible values: 2.4G or 5G|N/A|N/A|
|5|BSS|Basic Service Set of the connected client|N/A|N/A|
|6|Time Interval|See [Time Interval](#time-interval)|N/A|N/A|
|7|Connected Clients|See [Connected Clients](#connected-clients)|N/A|N/A|
|8|Max Simultaneous Clients|See [Max Simultaneous Clients](#max-simultaneous-clients)|N/A|N/A|
|9|Max Simultaneous Clients Timestamp|See [Max Simultaneous Clients Timestamp](#max-simultaneous-clients-timestamp)|N/A|N/A|
|10|Rejected Clients|See [Rejected Clients](#rejected-clients)|N/A|N/A|
|11|Another Operator|Field used to distinguish between different operators|N/A|N/A|

#### Time Interval

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.3.1.3|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.4.1.3|N/A|

#### Connected Clients

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.3.1.4|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.4.1.4|N/A|

#### Max Simultaneous Clients

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.3.1.5|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.4.1.5|N/A|

#### Max Simultaneous Clients Timestamp

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.3.1.6|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.4.1.6|N/A|

#### Rejected Clients

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.3.1.7|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.4.1.7|N/A|

### Client Errors Offload Structure

- Offload format: Tab-separated CSV file
- Offload folder: **RCCV Data Offload Folder**
- Offload file structure: `<DMAID>.<EID>.CMS.ClientErrors.<OPERATOR>.current.csv`
  - DMAID: DMA ID where the CM collector element is located.
  - EID: Element ID of the CM collector element.
  - OPERATOR: Operator assigned to the CMs available if the offload file.

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|SAPID|Service Access Point ID|N/A|N/A|
|2|Timestamp|Time of polling|N/A|N/A|
|3|MAC Address CM|Cable Modem MAC address|N/A|N/A|
|4|Frequency Access Point|Possible values: 2.4G or 5G|N/A|N/A|
|5|BSS|Basic Service Set of the connected client|N/A|N/A|
|6|Error Type|Specific error type encountered|N/A|N/A|
|7|Rejected Clients|See [Rejected Clients](#rejected-clients-client-errors)|N/A|N/A|
|8|Another Operator|Field used to distinguish between different operators|N/A|N/A|

#### Rejected Clients (Client Errors)

|Wifi Frequency|SNMP OID|OID Description|
|--------------|--------|---------------|
|2.4G|1.3.6.1.4.1.35604.1.19.51.5.5.2.1.2|N/A|
|5G|1.3.6.1.4.1.35604.1.19.51.5.6.2.1.2|N/A|

### Connected Powerline Offload Structure

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|SAPID|Service Access Point ID|N/A|N/A|
|2|Timestamp|Time of polling|N/A|N/A|
|3|MAC Address CM|Cable Modem MAC address|N/A|N/A|
|4|MAC Address Powerline|MAC address of the connected powerline device|1.3.6.1.4.1.35604.1.19.62.1.1.6.1.2|N/A|
|5|Location|Location of the connected powerline device|1.3.6.1.4.1.35604.1.19.62.1.1.6.1.3|N/A|
|6|Vendor|Vendor of the connected powerline device|1.3.6.1.4.1.35604.1.19.62.1.1.6.1.4|N/A|
|7|Firmware|Firmware version of the connected powerline device|1.3.6.1.4.1.35604.1.19.62.1.1.6.1.5|N/A|
|8|Chipset|Chipset of the connected powerline device|1.3.6.1.4.1.35604.1.19.62.1.1.6.1.6|N/A|
|9|Tx|Transmit power of the connected powerline device|1.3.6.1.4.1.35604.1.19.62.1.1.6.1.10|N/A|
|10|Rx|Receive power of the connected powerline device|1.3.6.1.4.1.35604.1.19.62.1.1.6.1.11|N/A|
|11|Another Operator|Field used to distinguish between different operators|N/A|N/A|
|12|n CPE Client|Number of connected CPE clients (1.n Mac)|1.3.6.1.4.1.35604.1.19.62.1.1.7.1.2|N/A|

### LAN User Offload Structure

- Offload format: Tab-separated CSV file
- Offload folder: **RCCV Data Offload Folder**
- Offload file structure: `<DMAID>.<EID>.CMS.LanUser.<OPERATOR>.current.csv`
  - DMAID: DMA ID where the CM collector element is located.
  - EID: Element ID of the CM collector element.
  - OPERATOR: Operator assigned to the CMs available if the offload file.

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|SAPID|Service Access Point ID|N/A|N/A|
|2|Timestamp|Time of polling|N/A|N/A|
|3|MAC Address CM|Cable Modem MAC address|N/A|N/A|
|4|MAC Address LAN|MAC address of the connected LAN device|1.3.6.1.4.1.35604.1.19.201.1.1.1.3|N/A|
|5|LAN Interface|Interface of the connected LAN device|1.3.6.1.4.1.35604.1.19.201.1.1.1.4|N/A|
|6|Another Operator|Field used to distinguish between different operators|N/A|N/A|

### Powerline Network Offload Structure

- Offload format: Tab-separated CSV file
- Offload folder: **HGW Data Offload Folder**
- Offload file structure: `<DMAID>.<EID>.CMS.PowerlineNetwork.<OPERATOR>.current.csv`
  - DMAID: DMA ID where the CM collector element is located.
  - EID: Element ID of the CM collector element.
  - OPERATOR: Operator assigned to the CMs available if the offload file.

|Item|Field|Description|SNMP OID|SNMP OID Description|
|----|-----|-----------|--------|--------------------|
|1|SAPID|Service Access Point ID|N/A|N/A|
|2|Timestamp|Time of polling|N/A|N/A|
|3|MAC Address CM|Cable Modem MAC address|N/A|N/A|
|4|Polling Interval|Interval at which the data is polled|1.3.6.1.4.1.35604.1.19.62.1.1.2.0|N/A|
|5|HPAV Network|Status of the HPAV network|1.3.6.1.4.1.35604.1.19.62.1.1.4.0|N/A|
|6|HPAV CCO|Status of the HPAV CCO|1.3.6.1.4.1.35604.1.19.62.1.1.5.0|N/A|
|7|Another Operator|Field used to distinguish between different operators|N/A|N/A|
