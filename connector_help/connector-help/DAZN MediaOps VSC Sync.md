---
uid: Connector_help_DAZN_MediaOps_VSC_Sync
---

# DAZN MediaOps VSC Sync

This connector will send HTTP POST messages to the AVOS system to keep it up to date with changes in dataminer.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |<ul><li>Handle job updates</li><li>Force Update Avos</li></ul>         |-         |-         |

### Product Info

|Range  |Supported Firmware  |
|---------|---------|
|1.0.0.x     |TBD         |

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
  - **IP port**: [The IP port of the destination. (default: *80*)]
  - **Device address**: [The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.]


### Initialization

The API token needs to be filled in into the Setup page.

### Redundancy

There is no redundancy defined.

## How to use

When a job is created a InterApp call is performed on the connector. The connector will add this call to an internal buffer and send this request over to AVOS. When the POST fails it will be added into the Failed Post Requests tabel. Every 10s this will be retried. 
There is also a max age to maintain this table, if there are records exeding this age they are removed.


### Notes

This Connector is designed to work with the DZN-UDAPI-AVOS automation script and a CRUD script which still needs to be designed.