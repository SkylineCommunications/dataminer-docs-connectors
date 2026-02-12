---
uid: Connector_help_Telenor_Channel_Correlation_Service_Broadcast_Technical
---

# Telenor Channel correlation Service Broadcast

## About

In the Telenor DMS, a service is created for each available broadcast channel. The service contains all the elements that contribute to the broadcast channel (IPTV, DVB-C, etc.). The **Telenor Channel correlation Service Broadcast** service protocol lists all the alarms in those elements and compares them with a list of rules defined by the operator. If a rule matches the current set of alarms, a new correlated alarm describing the state of the service is created.

## Configuration

### Connections

#### Virtual Connection - Main

This connector is a service connector and does not require any input during element creation.

## How to Use

The **General** page lists all the alarms present in the service.

The **Rules** page contains a table listing all the rules created by the operator. Rules can be added and removed using a context menu.

If the current set of alarms matches with one of the rules, a correlated alarm will be added in the **Correlated Alarms** table on the **Alarm** page.
