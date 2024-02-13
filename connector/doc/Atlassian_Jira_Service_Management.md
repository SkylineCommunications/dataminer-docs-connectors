---
uid: Connector_help_Atlassian_Jira_Service_Management
---

# Atlassian Jira Service Management

This connector is polls all issues and requests for Jira projects within a domain. With it, you can also use it to create simple issue tickets on a Service Desk.

## About

### Version Info

| Range            | Key Features | Based on | System Impact |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main] | Initial version. | -           | -                |

### Product Info

| Range | Supported Firmware |
|-----------|------------------------|
| 1.0.0.x   | -                     |

### System Info

| Range | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                    | -                      |

## Configuration

### Connections

#### HTTP Main Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: *443*).
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

Fill in the **Username** and **Password** on the General page. Basic authentication with passwords is deprecated and instead of the password an **API token** **needs to be used** (see also [Manage API tokens for your Atlassian account \| Atlassian Support](https://support.atlassian.com/atlassian-account/docs/manage-api-tokens-for-your-atlassian-account/)).

### Redundancy

There is no redundancy defined.

## How to use

The element polls all service desks for the environment specified in the URL of the element. This includes the **Service Desks**, **Queues**, and **Issues**. You can choose to Enable/Disable polling of certain Queues.

From the **Issues** page, it is possible to create a small issue given some input data. 
If you'd like to instead, by following the given format in the API documentation for [Create Request](https://developer.atlassian.com/cloud/jira/service-desk/rest/api-group-request/#api-rest-servicedeskapi-request-post), you can use an Automation Script to set PID 2 with your own JSON data.
