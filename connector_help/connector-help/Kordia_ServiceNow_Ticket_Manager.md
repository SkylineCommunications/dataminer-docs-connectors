---
uid: filename_using_underscores
---

# Kordia ServiceNow Ticket Manager

This connector is used to interact with the ServiceNow Application used by Kordia. It works with an Automation Script and Correlation Rules that use DataMiner alarming capabilities to create, update and delete incidents in their system according to specific business rules provided by Kordia.

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

#### HTTP

This connector is a HTTP type connector. Besides the **IP Address** and **Port** needed to create the element, a couple of other Parameters should be filled in the element to allow authentication with the ServiceNow Application. Please see below [Initialization](###Initialization) page.

### Initialization

In the **Config** page of the element you need to fill in the **Client ID**, **Client Secret** and **Refresh Token**. These will be used to establish authentication with the ServiceNow application and allow ticket updates afterwards. On top of that the Correlation Rule folder must be filled in. All correlation rules that can trigger Ticket updates should be under the same folder.

### Redundancy

No redundancy.

### Automation Scripts

Even though no Automation Scripts are mandatory, in order to facilitate the solution an Automation Script named **KOR-Send-ServiceNow-Request** is used to send the Alarm data from the Correlation Rule to the element. Such Automation Script also contains an input parameter that will be used as Impact Description in the Ticket creation.

### Correlation rules

Correlation Rules should be created in order to create/update/delete tickets based on DataMiner alarming. Taking into account Kordia's setup of Customers and Services being represented as DataMiner services, and the fact that each Customer may contain one or more Services, the Correlation rule should be created to monitor a DataMiner service representative of a Kordia Customer. An example can be found below.

[ADD IMAGE HERE]

## How to use

Besides the [Initialization](###Initialization) procedure, no other procedures are needed in order to get the Element running.

### Page Overview

#### General
In the **General** page a Statistics group can be found. That contains data related to the amount of incidents processed during the day and from the previous days. The idea is to have the possibility of tracking how many incidents were created per day as well as understanding behavior on a per-day basis. This page also contains a Logger table that has the POST request data sent and the response received from the ServiceNow Application. This can be helpful to understand message exchange and easily check any communication issues. This is saved directly to Elastic DB and is autocleared every 7 days.

#### Tickets

This page contains toggle buttons for Auto-Clear functionality of the Tickets table and also for the flapping functionality.

Flapping Window is used for cases where DataMiner alarms are flapping but incidents must not be closed if such flapping window has not passed. This reduces the number of false positives/negatives in the operation. This also helps us to calculate the correct Duration of an incident as it can be seen in the Tickets table.

The Tickets table contains information of Tickets that have been created by DataMiner based on the Correlation Rules created.

#### Config

Config page contains all the necessary parameters to establish Authentication with the ServiceNow Platform and other general configurations.
