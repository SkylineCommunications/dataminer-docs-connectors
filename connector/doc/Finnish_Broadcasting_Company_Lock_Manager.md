---
uid: Connector_help_Finnish_Broadcasting_Company_Lock_Manager
---

# Finnish Broadcasting Company Lock Manager

This connector is **obsolete** and has been replaced by the more generic [Skyline Lock Manager](xref:Connector_help_Skyline_Lock_Manager) connector. It is no longer recommended for use in new solutions.

This connector was used in the YLE Media Services solution to hold locks for orders and events.

## About

### Version Info

| Range              | Features        | Based on | System Impact |
|--------------------|-----------------|----------|---------------|
| 1.0.0.x [Obsolete] | Initial version | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components                                                                                           | Exported Components |
|---------|-----------------|---------------------|-------------------------------------------------------------------------------------------------------------|---------------------|
| 1.0.0.x | No              | Yes                 | - *Skyline.DataMiner.ConnectorAPI.FinnishBroadcastingCompanyLockManager* NuGet package<br>- YLE MS Solution | -                   |

## Configuration

### Connections

#### Virtual Connection - Main

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

No additional configuration of parameters is required in a newly created element. However, you can optionally define the amount of time after which the locks are automatically released (1 hour by default).

## How to use

The connector only works in conjunction with the *Skyline.DataMiner.ConnectorAPI.FinnishBroadcastingCompanyLockManager* NuGet package. This package is used from an Automation script or connector to lock and unlock orders and events. Internally, InterApp messages are used to facilitate the communication.

The locks are stored in memory by an element using this connector.

The active locks are visible on the General page of the element. Clicking the *Release Lock* button will release the lock.

> [!NOTE]
> Requesting or releasing a lock on an order will update the `IsLocked` reservation property accordingly. The property changes are triggered from the connector.

### Example

```csharp
using Skyline.DataMiner.ConnectorAPI.FinnishBroadcastingCompanyLockManager;

var element = IDms.GetElementsByProtocol(LockManagerElement.LockManager_ProtocolName).First();
LockManagerElement cachedLockManagerElement = new LockManagerElement(IDms.Connection, element.AgentId, element.Id);

LockManagerElement.LockOrder(orderId, username);
LockManagerElement.LockEvent(eventId, username);

// Do logic here while objects are locked

LockManagerElement.UnlockOrder(orderId);
LockManagerElement.UnlockEvent(eventId);
```
