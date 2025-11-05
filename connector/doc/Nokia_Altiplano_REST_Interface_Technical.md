---
uid: Connector_help_Nokia_Altiplano_REST_Interface_Technical
---

# Nokia Altiplano REST Interface

## About

The **Nokia Altiplano REST Interface** connector is an integral component of the Nokia Altiplano solution. It is responsible for receiving and executing API requests initiated by the solution. 

This connector serves as the exclusive interface within the platform for directly executing API requests on the target API.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.
- **Device address**: The bus address of the device. If the proxy server has to be bypassed, specify *BypassProxy*.

### Initialization

Upon creation of the element, the user must configure the following parameters located in the **Configuration** page under the **Altiplano REST Endpoint** section:

- **Polling Type**: Specify the HTTP connection protocol to be used as a prefix in request URLs. Supported values are HTTP and HTTPS.
- **Username**: Enter the device username required for authentication during the login request. 
- **Password**: Enter the device password required for authentication during the login request.
- **Endpoint *(optional)***: - Provide the endpoint IP address or hostname in the format ip:port or hostname:port. If this field is left blank, the element will default to the endpoint specified in its properties.

Additionally, users can enable or disable specific API requests that the element is permitted to execute. These options are available in the **Configuration** page under the **Inventory Queries** section.

## How to use

### Configuration

On this page, the user is able to define essential parameters for the HTTP driver. The following sections are available for setup: 

- **Endpoint connection**: Configure the connection parameters used for API communication, including: **Polling Type**, **Endpoint**, **Username** and **Password**.
- **Inventory Queries**: Enable or disable specific API queries the element can execute.
- **System Credentials**: Provide credentials required for system-level access: **System Username** and **System Password** parameters. 

Additionally, users can specify an export folder used to store files generated from API responses. This folder can be configured as either:

- **Local Folder**: Accessible directly from the host system.
- **Remote Folder**: Requires valid system credentials for authentication and access.

### Inventory

This page displays a table of all queries received and executed by the element. This inventory provides visibility into the operational history and status of API interactions.

- **Last API Table Update**: Indicates the timestamp of the most recent update to the **API Requests Inventory** table. Updates are triggered by job completions, new entries, or data processing events.
- **Max API Jobs Recorded**: Defines the maximum number of records to retain in the **API Requests Inventory** table. Once the limit is reached, older entries are automatically removed.

### InterApp Messages

This page provides visibility into the InterApp communication activity of the element. The displayed elements are:

- **Last InterApp Message**: Indicates the timestamp of the most recent update to either the Inbound or Outbound table.
- **Max InterApp Messages Recorded**: Defines the maximum number of records to retain in each table. Once the limit is reached, older entries are automatically removed.
- **Inbound Table**: Displays messages received by the element via InterApp. 
- **Outbound Table**: Displays messages sent by the element via InterApp.
