---
uid: Connector_help_ONATi_Splunk_Monitoring
---

# ONATi Splunk Monitoring

The Splunk Monitoring connector can be used to periodically fetch and analyze messages related to errors, failures, configuration changes, and severe failures.

The connector uses the search module of the extensive Splunk platform REST API.

## About

### Version Info

| Range | Features | Based on | System Impact |
|--|--|--|--|
| 1.0.0.x [SLC Main] | - Error and configuration change reporting.<br>- Critical and warning message monitoring by host/IP. | - | - |

### Product Info

The table below references the Splunk Enterprise firmware.

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
- **IP port**: The IP port of the destination (default: *8089*).

### Initialization

When you have created the element, you will need to specify valid credentials to connect to the Splunk server. To do so, go to the **General** page, fill in the **Username** and **Password**, and click the **Login** button. This will save the session key, which will later be used for all the search requests.

In order for the connector to poll tables correctly, for each table, the **search name** parameters also need to be set to the appropriate saved search names found in the Splunk Enterprise portal or through the Splunk API. These parameters are:

- Error Search Name (General page)
- Commits Search Name (General page)
- Critical Host Stats Search Name (Statistics page)
- Warning Host Stats Search Name (Statistics page)

## How to use

The Splunk Monitoring connector will poll predefined searches saved in Splunk Enterprise through the REST Splunk API. On the **Errors** and **Commits** pages, it will display the corresponding tables.

- The **Errors** table displays all Splunk entries that contain the words *error*, *failed*, or *severe* in a predefined past time slot. The error identifier, alongside with the IP of the host where the error occurred, will uniquely identify an entry. For each entry, you can find the first and the latest reporting of that error, the number of times the error appeared, and a more verbose message related to the error similar to the ones found in the logs.

- The **Commits** table is similar, but instead of errors it reports configuration commits made to certain devices in the system.

Another functionality of the connector is statistics. Splunk search will retrieve all the host IPs and count the number of messages containing the words "critical" or "warning" over the course of a time slot defined in the Splunk Enterprise saved search. Results will be saved in the **Critical Hosts** and **Warning Hosts** tables on the **Statistics** page.

## Notes

The data from each table is erased at around midnight local time.
