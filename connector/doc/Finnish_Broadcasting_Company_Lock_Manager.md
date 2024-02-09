---
uid: Connector_help_Finnish_Broadcasting_Company_Lock_Manager
---

# Finnish Broadcasting Company Lock Manager

This connector is used in the YLE Media Services solution to hold locks for Orders and Events.

## About

### Version Info

|Range  |Features  |Based on  |System Impact  |
|---------|---------|---------|---------|
|1.0.0.x [SLC Main]     |Initial version      |-         |-         |

### System Info

|Range  |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|---------|---------|---------|---------|
|1.0.0.x    |No       |Yes         |<ul><li>Skyline.DataMiner.ConnectorAPI.FinnishBroadcastingCompanyLockManager</li><li>YLE MS Solution</li></ul>           |   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

No additional configuration of parameters is necessary in a newly created element. You can optionally define the amount of time after which the locks are automatically released (1h by default).

### Redundancy

There is no redundancy defined.

## How to use

The connector only works in conjunction with the Skyline.DataMiner.ConnectorAPI.FinnishBroadcastingCompanyLockManager NuGet package. This package is used from an Automation Script or Connector to lock and unlock Orders and Events. Internally InterApp is used to facilitate the communication. These locks are stored in memory by an element using this connector. 

The active locks are visible on the General page of the element. Clicking the "Release Lock" button will release the lock.

> [!NOTE]
> Requesting or releasing a lock on an Order will update the `IsLocked` reservation property accordingly. The property changes are triggered from the connector.

### Examples

```
using Skyline.DataMiner.ConnectorAPI.FinnishBroadcastingCompanyLockManager;

var element = IDms.GetElementsByProtocol(LockManagerElement.LockManager_ProtocolName).First();
LockManagerElement cachedLockManagerElement = new LockManagerElement(IDms.Connection, element.AgentId, element.Id);

LockManagerElement.LockOrder(orderId, username);
LockManagerElement.LockEvent(eventId, username);

// Do logic here while objects are locked

LockManagerElement.UnlockOrder(orderId);
LockManagerElement.UnlockEvent(eventId);
```