---
uid: Connector_help_Ceiton_Resource_Planning_Technical
---

# Ceiton Resource Planning

This connector is used to store information from the Ceiton Resource Planning software solution. This software can be used to plan tasks into projects.

## About

The connector regularly polls the Ceiton Resource Planning endpoint for projects and products.
Additionally, it can receive unsollicited notifications from the Ceiton Resource Planning software through a web service hosted by the connector.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination (default: 9995).
- **Bus address**: If the proxy server has to be bypassed, specify *bypassproxy*.

### Initialization

In order to receive notifications from Ceiton, some settings need to be configured in the connector. These can be found on the **Notifications** page and include the **endpoint URL** to which the web service listens for incoming notifications, the **port** that the web service will use and the **type** of protocol. When **HTTPS** is selected as protocol, you will need to select a certificate that is installed on the system.

Enabling the web service is done through the **notifications status** parameter. When the web service is enabled, the **Web Service Status** should be *Opened*. If this is not the case, something may be wrong with the configuration. For example, another service in the system may be using the same port.

### Redundancy

Redundancy is not defined in the connector.

### Logging Configuration

As of version 1.0.1.8, the connector support persistent logging. This allows writing logs that persist when the element restarts.
The files created by the persistent logging have the following name template: `C:\Skyline DataMiner\Logging\[element name]_[suffix].txt`.

The logging behavior can be configured on the *Logging Configuration* sub-page using the following parameters:

- **Status**: Enables or disables the persistent logging.
- **Logging Level**: Defines the minimum level of logs that should be stored persistently.
- **Max Log File Size**: Defines the maximum size (in MB) of a single log file. When the size is exceeded, a new log file is created.
- **Max Log File Count**: Defines the maximum number of log files that are kept. When the number of log files exceeds this value, the oldest log file is re-used and its logs overwritten.
- **Log File Name Suffix**: Sets the suffix of the log file name in `C:\Skyline DataMiner\Logging\[element name]_[suffix].txt`.

## How to Use

When the connector receives a notification, the notification is parsed and the information is stored in the applicable tables.

Every 5 minutes, there is a check if the tasks and external requests are stored longer than the times defined in the parameters **Remove Tasks After** and **Remove External Requests After**. If they are, these tasks or requests are removed.

If a product is not referenced by a product task, the product is removed. If a project is not referenced by a product or project task, the project is removed.

In order to actively poll a product or project, an external request has to be made. This is done by writing a JSON serialized ExternalRequest (see ExternalRequests namespace in QA1) to parameter 850. When a valid external request is received, an entry is added to the **External Requests** table and the connector will try to poll the project or product with the provided values. If the request fails or no information is returned in the request, the status of the external request will be set to *Failed*, otherwise if will be set to *Success* and the requested resource will be available in the **Project** or **Product** table.
