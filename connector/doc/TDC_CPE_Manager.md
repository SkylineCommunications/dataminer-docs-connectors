---
uid: Connector_help_TDC_CPE_Manager
---

# TDC CPE Manager

The **TDC CPE Manager** is part of a CPE setup and is responsible for aggregating the data and providing the user interface. It works together with the following connectors:

- **CISCO CMTS**
- **Generic DOCSIS Cable Modem Collector**
- **Generic DOCSIS eMTA Collector**
- **Generic IP Resolve JSON**
- **Huawei MA5800-MA5633**
- **Skyline IAM Database**
- **Skyline IAM DB Provision**
- **TDC Humax STB Collector**
- **TDC OLT CM Collector**
- **Teleste Amplifier Collector**

## About

### Version Info

| Range                | Key Features                                        | Based on | System Impact             |
|--------------------------|---------------------------------------------------------|--------------|-------------------------------|
| 1.0.0.x **\[Obsolete\]** | Initial version                                         | -            | -                             |
| 3.0.1.x **\[Obsolete\]** | New CPE integration                                     | 3.0.0.4      | -                             |
| 3.0.2.x **\[SLC Main\]** | Added CpeConfigHelper to get and set CPE configuration. | 3.0.1.25     | Increased minimum DMA version |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components                         | Exported Components     |
|-----------|---------------------|-------------------------|-------------------------------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                                         | -                       |
| 3.0.1.x   | No                  | Yes                     | -                                         | -                       |
| 3.0.2.x   | No                  | Yes                     | TDC OLT CM Collector connector (view tables) | -                       |

## Installation and configuration

### Configuration of elements

Two types of elements are needed for this setup:

- A single front-end element (CPE FE), responsible for aggregating data at the top levels.
- Multiple back-end elements (CPE BE), each responsible for some OLT devices. These elements will perform the aggregation of the data coming from the collector elements.

### Configuration of parameters

The CPE Manager's Data Display pages are not intended to be opened. Instead, any configuration should be performed via a visual overview or multiple set.

### Configuration of offload

The following parameters can be set via **multiple set** in order to configure the offload mechanism to all related elements:

- **Offload CMC State**: Enables or disables the offload CMC data mechanism. Default value: *Disabled*.

- **Offload AMP State**: Enables or disables the offload AMP data mechanism. Default value: *Disabled*.

- **Offload CMC Cleanup State**: Enables or disables the file cleanup mechanism.
  - If this parameter is enabled, all files in the **Offload CMC Directory** that are older than the age defined in the **Offload** **File Age Threshold** parameter will be deleted.
  - This parameter is automatically enabled when the **Offload CMC State** is also enabled.
  - Default value: *Disabled*.

- **Offload CMC Directory**: The root directory where the offload files will be stored.

- The directory can be a shared folder. The credentials for the folder can be set using the **Offload Shared Folder Username** and **Offload Shared Folder Password** parameters.
  - A folder will be created per OLT with its name - the **OLT Name.**
  - Default value: *\\80.62.121.234\c\$\Skyline_Data\BE Manager Offload\\*

- **Offload AMP Directory**: The root directory where the offload files will be stored.
  - The directory can be a shared folder. The credentials for the folder can be set using the **Offload Shared Folder Username** and **Offload Shared Folder Password** parameters.
  - A folder will be created per OLT with its name - the **OLT Name.**
  - Default value: *\\80.62.121.234\c\$\Skyline_Data\AMP\\*

- **Offload File Age Threshold**: Determines for how long files are stored in the **Offload CMC Directory** before they are deleted to free up space.

- Range between *8 hours* and *1 year*, with 8-hour increments.
  - Default value: *2 weeks*

- **Force Offload / Offload To Disk**: Set this button to manually execute the offload of the files, regardless of both **Offload State (CMC/AMP)** values.

- **Debug Log Times**: Enables or disables extra logging related to the offload.

- If this parameter is enabled, upon a successful offload, the time and number of rows will be added in the element's log.

- **Offload Config String \[table name\]**: Contains all the column parameters that should be offloaded for the related table (specified in brackets).

- Multiple columns can be specified, with a comma (",") as separator.
  - The primary key will always be offloaded as the first column.
  - Information template column names are not supported.

The offload will not occur to front-end managers.

The offload files will always contain the primary key of the tables and a column with the **OLT Name** linked to each entry.

The files will be separated per OLT, inside the **Offload CMC Directory** and **Offload AMP Directory**. This means that each file will only contain the entries of a table related to a single OLT.

## Usage

If you open the card for this element in Cube, the CPE interface will be displayed, with different chains providing a different topology view.

If you fill in one of the filters (on the left), the topology diagram view is displayed. If you click a KPI item in this diagram view, a pop-up window with parameters opens.

### AMP Chain Export

The **BE Managers** have the possibility to export AMP Chain data to be further ingested by the **CM Collectors** (*TDC OLT CM Collector*). This data is useful to map the CM's channels to amplifiers.

If **CM AMP Chain Export State** is *enabled*, the **BE Manager** elements will create these files in the directory specified as the **CM AMP Chain Export Folder**, during the full provisioning. The result status is displayed by the **CM AMP Chain Export Status** parameter.

A file is created per **CM Collector** and contains 2 columns: the cable modem *MAC addresses* and the respective *AMP Chains*. The files can be identified by the *dmaId/elementId* of the **CM Collector** element responsible for ingesting them.

Only the newest files will be ingested by the **CM Collector**. Older files are moved to a backup folder (under the original one).

For maintenance purposes, files older than 7 days are deleted.

## IAM DB

The entire CPE setup is provisioned via a MySQL database called IAM.

There is also a fully automatic system to create new elements, assign properties and place the elements in the correct views based on the info from the IAM DB. The connector responsible for this is **Skyline IAM DB Provision**.

### Configuration of IAM Database

- DB Server Settings:

- DB Name: IAM
  - Server Name: IP address
  - DB Username
  - DB Password

## KPIs & KQIs

Key Performance Indicators (KPIs) are calculated on different levels. Below, you can find an overview of the KPIs per level.

### Generic KPIs

| Description               | Information                                                           |
|-------------------------------|---------------------------------------------------------------------------|
| \#CM                          | Total number of cable modems                                              |
| \#eMTA                        | Total number of eMTAs                                                     |
| \#STB                         | Total number of STBs                                                      |
| \#Address                     | Total number of addresses                                                 |
| \#3.0CM                       | Total number of cable modems per DOCSIS type (2.0, 3.0 or 3.1)            |
| \#Reg 3.0CM                   | Total number of registered cable modems per DOCSIS type (2.0, 3.0 or 3.1) |
| \#CM Reg / \#CM Dereg         | Total number of registered / deregistered cable modems \[%\]              |
| %CM Reg                       | Deregistered cable modems / (registered + deregistered cable modems)      |
| \#CM Resp (Ping)              | Total number of cable modems responding to ping command                   |
| \#CM Data Unavail on CMTS     | Total number of cable modems that are found in the OLT/CMTS               |
| %CM Data Avail on CMTS        | Available cable modems / (available + unavailable cable modems) \[%\]     |
| Avg CM Jitter                 | Average jitter of cable modems \[ms\]                                     |
| Avg CM Latency                | Average latency of cable modems \[ms\]                                    |
| Avg CM Packet Loss Rate       | Average packet loss ratio of the cable modems \[%\]                       |
| \#STB img Dist Low            | Total number of STBs breaching the low quality threshold                  |
| \#STB img Dist Very Low       | Total number of STBs breaching the very low quality threshold             |
| Current STB img Dist Low      | \#STB image disturbance low / \#STB                                       |
| Current STB img Dist Very Low | \#STB image disturbance very low / \#STB                                  |

### Generic Channel KPIs

| Description | Information                           |
|-----------------|-------------------------------------------|
| \#Act Ch        | Total number of active channels           |
| Bitrate         | Calculated bitrate \[Mbps\]               |
| Cap             | Capacity \[Mbps\]                         |
| Load            | Bitrate / capacity \[%\]                  |
| Ch Util         | Channel utilization measured by OLT \[%\] |

### KQIs

| Description | Information                           |
|-----------------|-------------------------------------------|
| %DM DOCSIS Avail | DM DOCSIS availability [%] = (Aggregated device availability / aggregated subscribers) * 100<br><br>**DM device availability**<br><br> *Calculated by DataMiner: status if device is responding (i.e. not in timeout) and has operational status = ON. Operational status = ON if DataMiner element is in active state (i.e. not paused or stopped) and element severity &lt; Major.*<br><br>**Aggregated device availability** = DM device availability * (aggregated sum of device availability)<br><br>*This parameter is the sum of device availability of all equipment available below the current topology level multiplied with the device availability of the current topology level.*<br><br>*Note that if no aggregated sum of device availability values is available (NA), the default value 1 is used.*<br><br>**Aggregated subscribers**<br><br>*This parameter is the sum of subscribers (cable modems) of all equipment available below the current topology level.* |
| Exp %DM DOCSIS Avail /Network | Expected DM DOCSIS availability [%] = Smart baseline value of the %DM DOCSIS availability |
| Avg BB Avail /Network | Broadband availability, average [%] = DM DOCSIS availability / expected DM DOCSIS availability |
| Worst 2% BB Avail /Network | Broadband availability, worst 2% [%] = Average for 2% customers with worst availability<br><br>*Calculates the weighted average of the DM DOCSIS availability KQI for 2% of the total number of customers above the smart baseline.* |
| Avg Current TV Service Avail | Current TV service availability, average [%] = Weighted average availability from AMP up to CMC, OLT, region and TDC network.<br><br>***Base parameters:***<br><br>*Result of pre-configured measurements on the amplifier and comparison of the values with pre-defined output level thresholds. In case any of the thresholds is breached, the TV service is unavailable and the Current TV Service Unavailable parameter will be set.* |
| Worst 2% Current TV Service Avail /Network | Current TV service availability, worst 2% [%]<br><br>*Calculates the weighted average of the current TV service availability KQI for 2% of the total number of subscribers.* |
| Avg TV Service Avail | TV service availability, average [%] = Weighted average availability from AMP up to CMC, OLT, region and TDC network.<br><br>***Base parameters:***<br><br>*Result of pre-configured measurements on the amplifier and comparison of the values with pre-defined output level thresholds. In case any of the thresholds is breached, the TV service is unavailable and the TV Service Unavailable parameter will be set.* |
| Worst 2% TV Service Avail /Network | TV service availability, worst 2% [%]<br><br>*Calculates the weighted average of the TV service availability KQI for 2% of the total number of subscribers.* |
| Avg Worst 5% Current NQI /Network | Current network quality index, average worst 5% [%] = Average current NQI value of the worst 5% of segments (CMCs)<br><br>**Base parameters:***<br><br>*AMP Current NQI = The DataMiner amplifier collector compares the actual value with the expected value after each polling cycle. In case the expected value is breached, the current NQI reduction is set as 0%, otherwise it is set as 100%.* |
| Avg Worst 5% NQI /Network | Network quality index, average worst 5% [%] = Average NQI value of the worst 5% of segments (CMCs)<br><br>***Base parameters:***<br><br>*AMP NQI = 100 - sum of reductions if no incident available for the current timestamp and amplifier.*<br><br>*NQI reduction (penalty score)*<br><br>*The DataMiner amplifier collector compares the actual value with the expected value after each polling cycle. In case the expected value is breached, the NQI reduction is increased with the reduction value, otherwise the value will not be changed.*<br><br>*Note that DataMiner takes the complete interval into account in case thresholds are breached.*<br><br>*At the beginning of each month, the NQI reduction will be reset.* |
| Max Cap Load of a Segment - BB | Maximum capacity load of a segment (broadband) [%] = (äSEG<sub>OK</sub> / total segments) * 100<br><br>*SEG<sub>OK</sub> = 1 if (max capacity of segment - weekly peak hour traffic rate per segment) ò higher class of service*<br><br>*Max capacity of segment: Configurable per segment.*<br><br>*Weekly peak: Average of daily peaks within the week, excluding the highest and lowest.*<br><br>*Daily peak: Maximum of the parameter Bitrate of a segment per day.*<br><br>*Higher class of service is configurable.* |
| Max Cap Load of a Segment - VoD | Maximum capacity load of a segment (VoD) [%] = (äSEG<sub>OK</sub> / total segments) * 100<br><br>*SEG<sub>OK</sub> = 1 if (max capacity of segment - weekly peak hour traffic rate per segment) ò highest quality stream * 5*<br><br>*Max capacity of segment: Sum of bandwidth of all active EQAM channels linked to this segment.*<br><br>*Weekly peak: Average of daily peaks within the week, excluding the highest and lowest.*<br><br>*Daily peak: Maximum of the parameter Bitrate of a segment per day.*<br><br>*Highest quality stream: Currently approx. 8 Mbps, but the whole threshold (highest quality stream * 5) is configurable.* |
| Speed Success Rate | Speed success rate [%] = 100 - 100 * ( äC<sub>ij</sub> / än<sub>i</sub> )<br><br>*For every customer, per type of segment (US/DS/QAM/OFDM), this evaluates:*<br><br>*C<sub>ij</sub> = 1 if s<sub>i</sub>ò p<sub>j</sub> , 0 otherwise*<br><br>*s<sub>i</sub> = Spare capacity of segment*<br><br>*Spare capacity = Max capacity - weekly peak load*<br><br>*p<sub>j</sub> = Purchased speed per customer*<br><br>*än<sub>i</sub> = Total number of broadband customers (QAM: #2.0CM + #3.0CM, OFDM: #3.1CM)* |
| STB Img Dist Low /Network | Monthly calculation of total number of STBs with image disturbance low / total number of STBs |
| STB Img Dist Very Low /Network | Monthly calculation of total number of STBs with image disturbance very low / total number of STBs |

## Notes

As the data pages are not accessible, to provide an easier way to configure the settings, a custom visual overview can be used.
