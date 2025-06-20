---
uid: Connector_marketing_Skyline_Lock_Manager
---

# Skyline Lock Manager

## About

The Skyline Lock Manager connector allows managing of locks within a DataMiner system for any kind of object by providing a centralised manager accessible through a public API. 

## Key Features

- **DataMiner-system-wide locking**: any component in the DMS can request a lock for an object.

- **Lock any object type**: any real or imaginary object can be locked, as long as the lock requesters give it the same ID.

- **Link objects**: objects and their locks can be linked to eachother, allowing for a more in-depth lock management.

## Use Cases

### Updating a DOM instance

**Challenge**: Imagine two scripts, ran simultaneously on different agents, trying to update the same DOM instance. The risk exists that the second script overwrites the changes made by the first script.

**Solution**: By first requesting a lock for the DOM instance to the Skyline Lock Manager, both scripts know whether they can read and update the DOM instance, or if they have to wait until the lock becomes available.

**Benefit**: Zero risk of overwriting changes to the DOM instance.

### Writing to a file

**Challenge**: Imagine multiple element running the same connector, writing custom logging to the same hardcoded text file. In theory, multiple elements might be trying to write to the file at the exact same time, causing I/O exceptions.

**Solution**: By first requesting a lock for the file to the Skyline Lock Manager, all elements know whether they can write to file, or if they have to wait until the lock becomes available.

**Benefit**: Zero risk of I/O exceptions when writing to the same file.

## Technical Reference

### Prerequisites

**[Skyline Lock Manager ConnectorAPI Nuget](https://www.nuget.org/packages/Skyline.DataMiner.ConnectorAPI.SkylineLockManager/)** is needed for communication with this connector.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Skyline_Lock_Manager).