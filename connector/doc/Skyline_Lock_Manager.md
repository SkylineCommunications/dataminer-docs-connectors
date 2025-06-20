---
uid: Connector_help_Skyline_Lock_Manager
---

# Skyline Lock Manager

The Skyline Lock Manager connector allows managing of locks within a DataMiner system for any kind of object by providing a centralised manager accessible through a public API. 

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]|Initial version|-|-|


### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |
|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         | [Skyline Lock Manager ConnectorAPI Nuget](https://www.nuget.org/packages/Skyline.DataMiner.ConnectorAPI.SkylineLockManager/)        |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

On the *Configuration* page, two parameters should be configured according to the systems requirements:

- InterApp Timeout: a timespan used by the [Skyline Lock Manager ConnectorAPI Nuget](https://www.nuget.org/packages/Skyline.DataMiner.ConnectorAPI.SkylineLockManager/), indicating when communication with this element should time-out.
- Default Auto Lock Release Timespan: when no specific auto unlock timestamp is provided by the API, the value of this parameter will be added to the timestamp of reception of the lock request to define the actual auto unlock timestamp. 

### Redundancy

There is no redundancy defined.

## How to use

By using the [Skyline Lock Manager ConnectorAPI Nuget](https://www.nuget.org/packages/Skyline.DataMiner.ConnectorAPI.SkylineLockManager/), other components within the DataMiner system (e.g.: automation scripts, connectors, ...) can communicate with an element running this connector to request a lock for any kind of object.

The connector keeps track of which locks are taken, along with some metadata like the timestamp of when the lock was taken, as well as the context that holds the lock. This data is stored in memory and can be visualized in the *Locked Objects* table by pressing the *Refresh Table* button.
Element restart causes this data to be lost.

When an object has been locked, any incoming request for the same *Object ID* will be answered with the lock not being granted.