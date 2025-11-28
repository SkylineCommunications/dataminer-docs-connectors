---
uid: Connector_help_Newtec_Dialog_Time_Series_Database
---

# Newtec Dialog Time Series Database

## About

The Newtec Dialog NMS (Network Management System) is the unified management interface for the ST Engineering iDirect (formerly Newtec) Dialog satellite communication platform. It uses a Time Series Database (TSDB) to store performance metrics for monitoring and analysis.  

The Dialog NMS provides a single, unified interface for all configuration, monitoring, and troubleshooting operations across the entire Dialog platform, from small private hubs to large, globally distributed High-Throughput Satellite (HTS) networks. The Newtec Dialog Platform VSAT connector collects and organizes data from a Newtec Dialog platform that stores its metrics in a Time Series Database (TSDB, i.e. Influx DB). 

This connector retrieves data from the Newtec Dialog Platform via its REST API and via the TSDB API. Data from both sources is aggregated into the connector. 

The connector uses the following APIs: 

- Newtec Dialog Restful Standard API (Central Dialog NMS): Configuration data of the Dialog system is retrieved using this API. 
- Newtec Dialog TSDB API (Hub Gateway Database): Statistics, metrics of terminals and sat networks are retrieved using the Time Series Database API.

## Key Features

- **Monitor the config data from Dialog NMS**: Provides the configuration for all components of Dialog NMS i.e. Remotes, Satellite Networks, Beams, Service Profiles, Carriers, Pools, Gateway, Transponders, Hub Modules, etc.

- **Monitors and aggregates the Remote TSDB**

- **Monitors and aggregates the Network TSDB**

- **Ability to control the config API and TSDB API polling**

- **Polling and DVE separation**
  
- **Backpolling**

- **SNMP and Ping monitoring capabilities**

## Use Cases

### Use Case 1

**Challenge**: Monitoring Dialog terminal performance across multiple locations.

**Solution**: The connector aggregates configuration and performance data into a single element.

**Benefit**: Enables quick identification of issues and ensures consistent service quality.

### Use Case 2

**Challenge**: Detecting early signs of SatNet degradation before impacting customers.

**Solution**: The connector captures real-time network events and performance statistics. 

**Benefit**: Facilitates proactive maintenance and faster problem resolution using the standard features of trend and alarm templates.

### Use Case 3

**Challenge**: Monitoring aggregated network statistics that are required for the SLA purposes.

**Solution**: The connector provides aggregated statistics of a network by combining the network throughput into 95th percentile and max throughput calculations for a defined time period.

**Benefit**: Ensures proactive maintenance and minimizes SLA breaches by actively monitoring the metrics related to SLAs.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Newtec_Dialog_Time_Series_Database_Technical).
