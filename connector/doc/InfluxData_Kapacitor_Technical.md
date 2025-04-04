---
uid: Connector_help_InfluxData_Kapacitor
---

# InfluxData Kapacitor

This connector allows you to monitor alarms through InfluxData Kapacitor HTTP API.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |-         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |-         |   |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

  - **IP address/host**: [The polling IP or URL of the destination.]
  - **IP port**: [The IP port of the destination.]


### Redundancy

There is no redundancy defined.


## How to use

Alarms can be monitored in the General page. HTTP requests are used to retrieve alarms based on the URL specified in the configuration page.

URL configuration can be done manually by changing the "Alarm Request URL" which will overwrite the Topic ID and Min-Level settings. Or by providing Topic ID and Min-Level which will automatically build the expected request URL.

Under the Polling Configuration the automatic polling interval for the alarms can be set. Setting "State" toggle to Disabled will prevent the polling interval from polling the alarms (the Refresh on Demand button will still function normally).

Debug page displays the last requests response code and full raw response.

To see the actual response, a built-in DataMiner tool called Stream Viewer can be used. You can access it by right-clicking the element in the Surveyor and selecting View > Stream Viewer.
