---
uid: Connector_help_ONATi_Splunk_Monitoring
---

# ONATi Splunk Monitoring

Splunk Monitoring connector is responsible for periodical fetching and analyzing retrieved messages related to errors, failures, configuration changes and severe failures. 
The driver utilizes the search module of the extensive Splunk platform REST API.

## About

### Version Info


|Range					|Features																										|Based on		|System Impact		|
|-----------------------|---------------------------------------------------------------------------------------------------------------|---------------|-------------------|
|1.0.0.x [SLC Main]     |<ul><li>Error and configuration change reporting</li><li>Critical and warning monitoring by host/IP</li></ul>  |-				|-					|

### Product Info

The following table is referencing the Splunk Enterprise firmware.

|Range       |Supported Firmware      |
|------------|------------------------|
|1.0.0.x     | Up to 9.0.1            |


### System Info


|Range      |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|-----------|-----------------|---------------------|-------------------|----------------------|
|1.0.0.x    |No               |Yes                  |-                  |-                     |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: The polling IP or URL of the destination.
  - **IP port**: The IP port of the destination. (default: *8089*)

### Initialization

Before using the connector, user needs valid credentials to connect to Splunk server. Filling in the _Username_ and _Password_ on the **General** page and clicking the _Login_ button will save the session key, later used for all the search requests. 

In order for the driver to poll tables correctly, for each table, the _search name_ parameters will need to be configured to the appropriate saved search names found in Splunk Enterprise portal or through Splunk API. These parameters are: 
- Error Seach Name (**General** page)
- Commits Search Name (**General** page)
- Critical Host Stats Search Name (**Statistics** page)
- Warning Host Stats Search Name (**Statistics** page)


## How to use

Splunk Monitoring will poll predefined searches saved in Splunk Enterprise through their REST Splunk API. Two tables found on the **Errors** and **Commits** pages are _Errors_ and _Commits_, respectively. 

_Errors_ table displays all Splunk entries which contains words: _error_, _failed_ or _severe_ in a predefined past time slot. Error identifier, alongside with the IP of the host where the error occured, will uniquely identify an entry where a user can find the first and the lastest reporting of that error, number of times the error appeared, and a more verbose message related to the error, similar to the ones found in logs. 

_Commits_ table works similarly, but instead of errors it reports configuration commits made to certain devices in the system.

Another functionality of the driver is statistics. Splunk search will get all the host IPs and count the number of messages where words "critical" and "warning" have appeared over the course of a time slot defined in Splunk Enterprise saved search. Results will be saved in _Critical Hosts_ and _Warning Hosts_ tables found on the **Statistics** page.
## Notes

All data from every table will be erased at around midnight local time.
