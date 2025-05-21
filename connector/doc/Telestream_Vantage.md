---
uid: Connector_help_Telestream_Vantage
---

# Telestream Vantage

The Telestream Vantage software can be installed and run on a Windows server machine. This software is used to monitor and control Telestream clusters used for video transcoding. At this stage, only monitoring is implemented.

## About

This connector queries a SOAP interface available on the target machine.

Multiple different SOAP requests are daisy-chained to query for the list of configured workflows and jobs. Additional details are also retrieved for each **workflow** and **job** (including completion percentage and other metrics, such as the total execution time).

The connector also queries the Vantage SOAP interface for the various **servers** available in the cluster and retrieves information for each of these machines, including their **service list**, state, and metrics.

### Version Info

| Range | Description | DCF Integration | Cassandra Compliant |
|--|--|--|--|
| 1.0.0.x | Initial version | No | Yes |
| 1.0.1.x | Implemented redundant pooling | No | Yes |
| 1.0.2.x | Added unicode option. | No | Yes |
| 1.0.3.x | Added unicode option. Major logic refactor with performance improvements. Upgrading from 1.0.2.x to 1.0.3.x has no major impact, as only changes to the internal logic have been implemented. | No | Yes |
| 1.0.4.x  [SLC Main] | Changed the minimum required DataMiner version to 10.2.9.0 - 12190. | No | Yes |

### Product Info

| Range | Supported Firmware Version |
|------------------|-----------------------------|
| 1.0.0.x          | Vantage 6.3                 |
| 1.0.1.x          | Vantage 6.3                 |
| 1.0.2.x          | Vantage 6.3                 |
| 1.0.3.x          | Vantage 6.3                 |
| 1.0.4.x          | Vantage 6.3                 |

## Installation and configuration

### Creation

#### HTTP main connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*.
- **Port number**: The port of the connected device, by default *8676*.
- **Bus address**: By default, this field is filled in with "*ByPassProxy*". This is necessary to avoid network issues.

#### HTTP secondary connection

This connector has a secondary connection and requires the following input during element creation.

HTTP CONNECTION:

- **IP address/host**: The polling IP of the device, e.g. *10.11.12.13*.
- **Port number**: The port of the connected device, by default *8676*.
- **Bus Address**: By default, this field is filled in with "*ByPassProxy*". This is necessary to avoid network issues.

### Configuration of Redundant Polling

This connector supports redundant polling. If an HTTP request times out, a secondary connection will be used for a retry. In order to use this feature, you must configure the secondary HTTP connection.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

Two main sets of pages are available in the connector. One set displays the **cluster information** (**servers** and **services**) and the other displays the **workflows** and **jobs** information.

Each set consists of two pages, one displaying the information in a **tree view** and the other displaying the **source tables** that contain all the data retrieved from the server. Users can monitor either page according to preference.

### Domain Machines and Server Page

This page displays a list of **servers** available in the **domain**. For each server, a list of **services** is also displayed, along with all **service metrics**.

This page displays its data in a **tree view**.

### Domain Machines and Server Tables Page

This page displays the same data as the "Domain Machines and Server" page, but the data is displayed in a **table structure** instead of a tree view.

### Workflow and Jobs Page

This page displays a list of **workflows** that are configured on the cluster. For each retrieved **workflow**, a **list of jobs** is also retrieved, along with the **current completed percentage**. For each of these jobs, a **list of sessions** is also retrieved. This information contains a historical overview of each job with each different step.

This page displays its data in a **tree view** format.

### Workflow and Jobs Tables Page

This page displays the same data as the "Workflow and Jobs" page, but the data is displayed in a **table structure** instead of a tree view.

### Driver Configuration Page

This page allows you to filter the jobs by their present status, and filter the session by date.

These filters limit the information shown on the other pages according to the selected options.

### Request Queue and Tasks (range 1.0.3.x)

Range 1.0.3.x features a queue containing the current requests to be done. No priority ordering has been implemented. The requests are done by order of entry in the queue, so set requests do not get priority. To fill the request queue and process responses, independent tasks are used. Each task has a maximum lifetime of 15 minutes.
