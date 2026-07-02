---
uid: Connector_help_Telenet_CPE_Manager
---

# Telenet CPE Manager

The **Telenet CPE Manager** is part of the EPM (CPE) solution, and works together with the **Telenet CM Collector**, **Telenet STB Collector** and **Telenet eMTA Collector** connectors. This connector is responsible for aggregating the data and exposing the topology overview in Cube to end users.

## About

This connector can be used in two different roles: a **frontend** role and a **backend** role. When creating an element using this connector, the role of the element must be defined.

In a typical EPM solution, there will be one frontend element and multiple backend elements deployed across the DMS:

### Backend

- A backend element is responsible for one specific headend (city).
- The backend element aggregates data coming from the collector elements and distributes the online/offline traps from the CMTS. The backend elements are deployed per headend.
nd they are deployed per DMA.

### Frontend

- The frontend role is responsible for provisioning and distribution of the syslog messages, while the backend role is responsible for one headend and performs the aggregation of the data coming from the collector elements and the distribution of the online/offline traps from the CMTS.

- There is only one frontend element deployed across the DMS, which is responsible for retrieving information from all the backend elements and providing a complete overview of the topology.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| 2.1.0.x [Obsolete] | Initial version after POC. | No | No |
| 2.2.0.x [Obsolete] | Based on 2.1.0.30. Relabel for next version. | No | No |
| 2.2.1.x [Obsolete] | Based on 2.1.0.1. Store partition VOD/UAU and Channel file for STB provisioning. | No | No |
| 2.2.2.x [Obsolete] | Based on 2.2.1.3. Reporting of service changed on node and street level. | No | No |
| 3.0.0.x [Obsolete] | Based on 2.2.2.0. Feature 58 forward node name to CPE collectors. | No | No |
| 4.0.0.x [Obsolete] | Based on 3.0.0.1. Baseline changed. | No | No |
| 5.0.0.x [Obsolete] | Based on 4.0.0.0 Added ratings and VoD check in provisioning | No | No |
| 6.0.0.x | Complete redesign of the connector. In previous versions, the frontend contained all topology information, including all CPE MAC addresses. This was too much for one element to handle. All tables and their provisioning needed to be changed so it was possible to shift the topology from frontend to backend elements. Because of this redesign, this version is not compatible with previous versions. | No | No |
| 6.0.1.x | Based on 6.0.0.18. The SFR cluster only contains cable modems. The connector had to be adapted so the STB and eMTA were removed from the tables, the provisioning, and the collector elements. Only parameters were removed, so switching to this version with an existing element using the 6.0.0.x range is possible if necessary. | No | No |
| 6.0.2.x [SLC Main] | Based on 6.0.0.19. Removed VoD, BCQ and BO chains. Street level has been changed to Amplifier level and some KPIs have been removed from different levels. | No | No |

### Product Info

| Range | Device Firmware Version |
|--|--|
| x.x.x.x | This connector listens to incoming syslog messages. These do not have a firmware version. The incoming traps are from the generic MIB and also do not rely on a firmware version. |

## Installation and configuration

### Creation

#### Serial connection

This connector uses a serial connection to receive the SYSLOG messages, and requires the following input during element creation:

**Serial Connection:**

- **IP address/host**: The IP of the DMA where the SYSLOG messages are received.
- **IP Port**: The port that the connector will be listening to, by default *514*.

#### SNMP connection

This connector uses a Simple Network Management Protocol (SNMP) connection to receive SNMP traps coming from the CMTSs, and requires the following input during element creation:

**SNMP Connection:**

- **IP address/host**: 127.0.0.1.

**SNMP Settings:**

- **Port Number**: The port of the connected device, by default *161*.
- **Get community string**: The community string used when reading values from the device, by default *public*.
- **Set community string**: Not required as the connector does not perform sets.

### Frontend Configuration

#### Frontend offload parameters

- The CPE Manager's data pages are not intended to be displayed in DataMiner Cube. Instead, any configuration should be performed either through [multiple set](https://aka.dataminer.services/multiple-set) or via a Visio file linked to the element.

- The **CPE Manager Type** should be set to *Front-end* for the frontend element.

- **Ratings Offload Folder** contains the location of the offload files with the view ratings. **PROV Source Folder** contains the location of the provisioning files.

#### Frontend aggregation parameters

- **CPE Manager Chassis Aggregation**, **CPE Manager Street Aggregation** and **CPE Manager UAU Aggregation** should always be set to *Off* because the frontend does not contain data for these levels.

- **CPE Manager Aggregation State** can be set to *Active* to enable all aggregation. This parameter is automatically changed and set to *Hold* when provisioning is going on.

- **CPE Manager Region Aggregation** can be set to *On* to enable the aggregation on Telenet level.

- **Ratings Aggregation Timer State** can be set to *On* to enable the aggregation of the view ratings. The frontend manager will offload the view ratings every 15 minutes.

### Frontend provisioning parameters

When the provisioning files are processed, new data files will be available that the backend CPE manager elements can use to provision. These files will be retrieved through a shared folder. **Frontend Agent** contains the IP address, **Frontend Share Username**, **Frontend Share Password** and **Frontend Share Domain** contain the credentials of the shared folder.

You can start provisioning by setting the button **Start Provisioning** to *Now*. The backend elements and collectors will also provision. With **Allow Error in Provisioning Files**, you can define whether provisioning should continue when there are errors in the provisioning files. You can check if the provisioning files contain errors without actually provisioning by setting **Start Provisioning Check** to *Now*.

PROV Result Table and PROV Logging are both tables that contain more info about the provisioning. You can clear these tables by setting the buttons **PROV Clear Result Table** and **PROV Clear Logging Table** to *Now.*

### Backend Configuration

#### Backend offload parameters

- The **CPE Manager Type** should be set to *Back-end* for the backend elements.

- The parameter **Data Offload Folder** contains the location of the offload files with aggregation results.

- To enable sending traps to `Adlex Nouveau` per chassis, set the parameter **Chassis AN Enabled** to *Enabled*.

#### Backend aggregation parameters

- **CPE Manager RegionAggregation** should always be set to *off* because the backend does not contain data for these levels.

- To enable the aggregation that is executed every 5 minutes on different levels, set the parameters **CPE Manager UAU Aggregation**, **CPE Manager Chassis Aggregation** and **CPE Manager Street Aggregation** to *On*.

- To enable the OOS aggregation that is executed every minute, set the parameter **BE OOS Aggregation Timer State** to *On*.

- To enable the aggregation of the view ratings from the STB collectors every 5 minutes, set the **Ratings Aggregation Timer State** to *On*. These view ratings of all the backend managers will then be merged by the frontend manager every 15 minutes.

- To enable the offload of the node and the node frequency data every 15 minutes, set **Node-Offload Timer State** to *On*.

- To enable the calculation of the OOS rate every 2 minutes, set the **Change Rate Timer State** to *On*. This calculation is done on the Street and Node level for the OOS of CM, eMTA and STB.

#### Backend headend parameters

Fill in the headend name that the backend manager will be responsible for in the parameter **Backend Responsible for Headend**.

Add the DMAID/EID of the collectors in the parameters **Add Backend CM Collector**, **Add Backend STB Collector** and **Add Backend EMTA Collector**. This will add rows to the tables **Backend CM Collector Table**, **Backend STB Collector Table** and **Backend EMTA Collector Table**. You can remove these rows again with the **Remove Backend Collector** column in the table.

During provisioning, the backend manager will divide the number of CMTSs equally over the collector elements. The **Rearrange Collector Spreading** parameter should be used with extreme care, as this will reassign all MAC addresses, which could cause a huge load to remove and add everything to the collector elements. Once this configuration is done, the button **Send Config To Frontend** should be set to *Send*.

When the collector elements are not located on the same DMA as the backend manager element, they must be able to retrieve the provisioning data through a share folder. You can configure the credentials for this share folder with the parameters **Backend Share Username**, **Backend Share Password** and **Backend Share Domain**.

The **Frontend Agent ID** parameter needs to be filled in with the DMAID/EID of the frontend manager element, so that the backend manager knows to which frontend to send its configuration.

#### Backend alarm parameters

You can configure certain settings to influence the alarms.

With **Minimum \# CM Monitoring Threshold**, **Minimum \# MTA Monitoring Threshold**, **Minimum \# STB Monitoring Threshold** and **Minimum \# STB VoD Monitoring Threshold**, you can configure that there will only be an alarm if the parameter represents a minimum amount of CPEs.

With the **Correction Factor** parameters, you can adjust the normalization value per type of CPE and per level. This way, the normalization value can be adjusted throughout the day, because the load in the morning can be different (generate no alarm with this value) from the load in the evening (generate an alarm with this value).

#### Backend normalization parameters

The baseline values used for normalization are based on the trending values of the past days. The way the normalization is calculated is defined in the **Baseline Lookup Table**. You can fill in this table by setting the **Baseline** button either to the value *Import* to load the data from a CSV file, or to the value *Add* to manually add a row. This CSV file must have the name *BaselineInfo.csv* and must be stored in the folder *C:\Skyline DataMiner\Protocols\Telenet CPE Manager\Production*.

For most of the calculations, the trending database is queried. Out of these values, the median value is taken as baseline value. The OOS type will take the data of yesterday, and the other types will take the data of the past week.

The rows in the CSV file need to have the following format (semicolon-separated):

1. **PID**: PID of the parameter for which the normalization should be calculated.
1. **Table**: The table ID where the parameter is located.
1. **Nominal Column**: 1-based index where the nominal column is located.
1. **Total Column**: 1-based index where the total number of CPEs column is located (only used with OOS type).
1. **Multiplier/Default**: Default value when no trending found: Multiplier \* Total if OOS type or default value.
1. **Type**: Value 1 if OOS, otherwise other value.
1. **Description**: A description for this line.
1. **Pct Limit Jump**: Used in frequency calculations.
1. **Lower Limit**: Used in frequency calculations.
1. **Upper Limit**: Used in frequency calculations.

Because the frequency tables contain too much data in the database to be processed, a different approach is taken. Cumulative average values will be calculated during runtime without looking at the database. As long as the value is between "current baseline - Lower Limit" and "current baseline + Upper Limit", the average is calculated as the baseline value for the next day. If the value is outside these limits, then the baseline will increase or decrease once per day with a percentage of the upper or lower limit. Suppose, for example, that the baseline is 15, the Pct Limit Jump is 20 and the Upper Limit is 3. When the value is 19, then this is higher than 15+3, so the new baseline will increase with 20% of 3, or 0.6, which makes the new baseline value 15.6. If the next value is 20, this will have no effect on the baseline because there was already one jump this day. This way, we avoid that exceptional high values have too much influence on the average baseline calculation. When Upper Limit is not filled in, the same value as Lower Limit is taken.

## Usage

As described above, the data pages of the CPE Manager are not intended to be used.

If you open the card in Cube, the CPE interface will be displayed, with different chains/branches providing a different topology view.

If you fill in one of the filters (on the left side), the topology diagram view is displayed. If you click a KPI item in this diagram view, a pop-up window with parameters opens. In most of the cases, you can also click next to the diagram tab and display all the CMs/STBs or eMTAs that are under this topology level.

You can also right-click an alarm in Cube and select **Open** \>*CPE Manager element name*. This will open the CPE Manager with the filter already filled in at the right position, so the topology is immediately shown.

## Provisioning

The **frontend** manager element using this connector requires the CSV files mentioned below. The CSV files must be **semicolon-separated**. The connector will analyze these files and create new CSV files per headend, which the backend manager can pick up and use for provisioning.

### hfc_cpe_iaa.csv

- Node
- DS Group
- US Group
- House number
- House letter
- Letter box
- Street
- Postal
- City
- SAP ID
- Another Operator
- CM Mac
- INT line
- CM HW Type
- eMTA MAC
- eMTA lines
- \# of STB
- 18 + \# of STB; STB MAC

### GIGIntf.csv

- Chassis Name: The name of the chassis (CCAP/CMTS).
- Chassis Public IP: The public IP address of the chassis, which is used for the traps coming from the CMTS.
- Chassis Private IP: The private IP address of the chassis, which is used for the provisioning.

### Channel.csv

- Headend Name
- Packet
- Program
- Frequency
- Port
- Slot
- Ring

### Network.csv

File name: `NetworkBSR1.csv`

- Headend Name: The name of the headend (e.g., GENT, AALS, etc.).
- Service: The type of service (e.g., DOCSIS).
- Service element: The service specification (e.g., DOCSIS-3.0, DOCSIS-3.1, etc.).
- Chassis Name: The name of the chassis (e.g., `CAP70AALS01`, `CAP70AALS02`, etc.).
- RF Card Name: The name of the line card in the chassis (e.g., `CRDCAP70AALS01-09`).
- RF Port Name: The name of the RF port on the line card (e.g., `PRTCAP70AALS01-09-0U3-03`).
- DS/US RF Channel: The downstream or upstream RF channel on which the service is provided (e.g., `UChCAP70AALS01-09-CHID41`).
- DS/US RF Spectrum map: The spectrum map of the downstream or upstream RF channel on which the service is provided (e.g., `UCM-CAP70AALS01-09-U4`).
- DS/US group: The service group on which the service is provided (e.g., `UH70AALS193`).
- Node-ID1.Node-IDn: The nodes on which the service is provided, separated by a period (`.`) (e.g., `H70GA01AAC0`).

### UAUInfo.csv

- Node
- Sub UAU
- Main UAU
- Packet

### vod_buildout.csv

- Headend Name
- Node Name
- Frequency
- VOD RF Port
- VOD RF Card
- VOD Chassis Name
- VOD SG Group

## Generated Offload Files

- The CPE Manager (backend role) will generate offload files related to aggregated metrics calculated by the backend element and generated by the collector elements. These aggregated metrics will be combined with topology information and properties of the metrics (e.g. frequency, etc.) to provide a complete overview of the network and its performance.

>[!NOTE]
> Most of the aggregated information offloaded are related to node level.

- These files are tab-separated CSV files.

- Different types of offload entries will be offloaded in a single file.

In one single file, the backend manager will offload the node data as well as the frequency data. Depending on the type, there will be a different number of offloaded fields (tab-separated).


### Node data structure

- Timestamp: Timestamp when the entry was added to the offload file (format: YYYY-MM-DD HH:MM:SS)
- Node Name
- `#CM OOS`: Number of CMs that are out of service.
- `#MTA OOS`: Number of eMTAs that are out of service.
- `#eMTA OOS`: Number of eMTAs that are out of service.
- `#STB OOS`: Number of STBs that are out of service.
- `%CM With DS CR > T`: Percentage of CMs with downstream correctable errors greater than a predefined threshold.
- `%CM With DS UR > T`: Percentage of CMs with downstream uncorrectable errors greater than a predefined threshold.
- `%CM With US CR > T`: Percentage of CMs with upstream correctable errors greater than a predefined threshold.
- `%CM With US UR > T`: Percentage of CMs with upstream uncorrectable errors greater than a predefined threshold.
- `%MTA Not In Pass`: Percentage of MTAs not in pass state.
- `%MTA Not In Operational`: Percentage of MTAs not in operational state.
- `%STB With Restart`: Percentage of STBs that have restarted.
- `%CM With US Level > T`: Percentage of CMs with upstream level greater than a predefined threshold.
- `CM Avg RTT`: Average round-trip time for CMs.
- `{INFO_ID++}` *(fixed string)*

### Node CM DS frequency data structure

- `{REF_ID++}` *(fixed string)*
- `{INFO_ID}` *(fixed string)*
- Offload Type: Possible values: 5 or 6 or 11 or 12
- Frequency: Frequency in KHz
- Avg Level or Avg SNR or %CM With DS CR \> T or %CM With DS UR \> T

### Node CM US frequency data structure

- `{REF_ID++}` *(fixed string)*
- `{INFO_ID}` *(fixed string)*
- Offload Type: Possible values: 9 or 10 or 13 or 14
- Frequency (in KHz)
- Avg Level or Avg SNR or %CM With US CR \> T or %CM With US UR \> T

### Node STB frequency data structure

- `{REF_ID++}` *(fixed string)*
- `{INFO_ID}` *(fixed string)*
- Offload Type: Possible values: 1 or 2 or 3 or 7
- Frequency (in KHz)
- Avg Level or Avg SNR or Avg BER or %STB With Errors

## Generated view ratings offload CSV files

The frontend manager will offload the view ratings in two files. State offload will contain the number of STBs that are not watching a channel. View offload will contain the number of STBs that are watching a channel, as well as the exact channel and type. These files are semicolon-separated.

### State offload structure

- Timestamp (format: YYYY-MM-DD HH:MM:SS)
- Region
- `#STB Unknown State`
- `#STB Standby State`
- `#STB VOD State`

### View offload structure

- Timestamp (format: YYYY-MM-DD HH:MM:SS)
- Region
- LIVE or TSB or REC
- Channel
- `#STB`
