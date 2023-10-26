---
uid: Connector_help_Kordia_ServiceNow_Ticket_Manager
---

# Kordia ServiceNow Ticket Manager

This connector is used to interact with the ServiceNow Application used by Kordia. It works with an Automation script and Correlation rules that use DataMiner alarm capabilities to create, update, and delete incidents in their system according to specific business rules provided by Kordia.

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

#### HTTP Connection – Main

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

### Initialization

When you have created the element, go to the the **Config** page and fill in the **Client ID**, **Client Secret**, and **Refresh Token**. These will be used to establish authentication with the ServiceNow application and allow ticket updates afterwards.

In addition, you will need to fill in the **Correlation rule folder**. All Correlation rules that can trigger ticket updates must be in the same folder.

### Automation Scripts

While this is not mandatory, in order to facilitate the solution, an Automation Script named **KOR-Send-ServiceNow-Request** can be used to send the alarm data from the Correlation rule to the element.

This Automation script contains an input parameter that will be used for the impact description in the ticket creation.

### Correlation rules

Correlation Rules should be created in order to create/update/delete tickets based on DataMiner alarming. Taking into account Kordia's setup of Customers and Services being represented as DataMiner services, and the fact that each Customer may contain one or more Services, the Correlation rule should be created to monitor a DataMiner service representative of a Kordia Customer.

## How to use

### General Page

On this page, the **Statistics** section contains data related to the number of incidents processed during the current day and from the previous days. This makes it possible to track how many incidents were created per day as well as to understand behavior on a per-day basis.

This page also contains a logger table that has the POST request data sent and the response received from the ServiceNow application. This can be helpful for insight in the message exchange, so you can easily check any communication issues. This data is saved directly to the indexing database and is cleared automatically every 7 days.

### Tickets Page

On this page, the Tickets table displays information about the tickets that have been created by DataMiner based on the Correlation rules used with the connector.

Flapping Window is used for cases where DataMiner alarms are flapping but incidents must not be closed if such flapping window has not passed. A flapping incident is for example an alarmed interface that keeps switching between Up/Down in a short amount of time. This reduces the number of false positives/negatives in the operation and also helps us to calculate the correct Duration of an incident as it can be seen in the Tickets table.

The page also contains toggle buttons for auto-clear functionality of the Tickets table and also for the flapping functionality.

### Config Page

This page contains all the necessary parameters to establish authentication with the ServiceNow Platform, as well as other general settings.
