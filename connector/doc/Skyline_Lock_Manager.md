---
uid: Connector_help_Skyline_Lock_Manager
---

# Skyline Lock Manager

## About

The Skyline Lock Manager connector allows the management of locks within a DataMiner System for any kind of object by providing a centralized manager accessible through a public API.

## Key Features

- **DataMiner System–wide locking**: Any component in the DMS can request a lock for an object.

- **Lock any object type**: Any real or virtual object can be locked, as long as the lock requesters give it the same ID.

- **Priority levels for locks**: When requesting a lock, a priority level can be specified. This allows more important components to get a lock even when less important components already hold a lock for the same object.

- **Link objects**: Objects and their locks can be linked to each other, allowing more in-depth lock management.

- **Wait for lock to become available**: When initially a lock was not granted, the connector and API support waiting for that specific lock to get released.

## Use Cases

### Updating a DOM Instance

**Challenge**: Imagine two scripts, running simultaneously on different Agents, trying to update the same DOM instance. The risk exists that the second script overwrites the changes made by the first script.

**Solution**: By first asking the Skyline Lock Manager for a lock to the DOM instance, both scripts know whether they can read and update the DOM instance or if they have to wait until the lock becomes available.

**Benefit**: Zero risk of overwriting changes to the DOM instance.

### Writing to a File

**Challenge**: Imagine multiple element running the same connector, writing custom logging to the same hard-coded text file. In theory, multiple elements might be trying to write to the file at the exact same time, causing I/O exceptions.

**Solution**: By first asking the Skyline Lock Manager for a lock to the file, all elements know whether they can write to the file or if they have to wait until the lock becomes available.

**Benefit**: Zero risk of I/O exceptions when writing to the same file.

### Updating a Booking with a UI Script While the Booking Transitions to Ongoing

**Challenge**: Imagine a booking that is being updated by a UI script while at the same time the booking transitions to ongoing. There is a risk that the UI script overwrites the changes made by the transition to ongoing.

**Solution**: The UI script asks for a low-priority lock on the booking, while the script that is responsible for the transition to ongoing requests a high-priority lock. The scripts can then be developed in such a way that the UI script releases its lock when the booking transitions to ongoing, allowing the transition script to acquire the lock and make its changes.

**Benefit**: Scripts that cannot be retried can always execute, no matter which script has the lock.

## Technical Reference

### Prerequisites

To make sure other components in your DataMiner System can communicate with this connector, the **[Skyline Lock Manager ConnectorAPI Nuget](https://www.nuget.org/packages/Skyline.DataMiner.ConnectorAPI.SkylineLockManager/)** must be installed.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Skyline_Lock_Manager_Technical).
