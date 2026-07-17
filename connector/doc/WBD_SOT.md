---
uid: Connector_help_WBD_SOT
---

# WBD SOT

## About

The WBD SOT (Source of Truth) is Warner Bros. Discovery's central registry of network entries, keeping track of authoritative source information such as addressing and protection/redundancy details for the streams and devices used across their infrastructure.

This **WBD SOT connector** interacts with the WBD SOT API to synchronize this registry into DataMiner, giving operators a real-time, consolidated view of all registered entries.

## Key Features

- **Entry synchronization**: Keeps a local, up-to-date copy of every entry registered in the WBD SOT, including a full sync on startup and efficient incremental (cursor-based) updates afterwards.
- **Redundancy insight**: Displays both the primary and backup addressing (address, SSM, and port) configured for each entry, together with its protection scheme.
- **Connection & health monitoring**: Continuously reports the connection status to the WBD SOT API, along with API and application version metadata.
- **Configurable polling**: Lets you enable/disable and tune the polling frequency of each underlying API call independently.

## Use Cases

### Centralized Source of Truth Visibility

**Challenge**: Operations teams need a single, reliable place to verify which entries (sources/devices) are registered, how they are addressed, and whether they are protected, without having to query the WBD SOT system directly.

**Solution**: The connector automatically retrieves and maintains the full list of entries from the WBD SOT, exposing name, protection scheme, primary and backup addressing (address, SSM, port), and creation/update timestamps in a clear table.

**Benefit**: Gives operators immediate insight into the authoritative state of every entry, reducing the need for manual lookups and helping to quickly spot missing, outdated, or misconfigured entries.

### Reliable, Low-Impact Synchronization

**Challenge**: Repeatedly pulling the entire entry list from the WBD SOT can be inefficient and puts unnecessary load on the source system.

**Solution**: After an initial full synchronization, the connector uses cursor-based incremental syncs to fetch only the changes that occurred since the last update.

**Benefit**: Keeps DataMiner's view of the WBD SOT continuously up to date while minimizing API usage and load on the WBD SOT system.

## Technical Reference

> [!NOTE]
> For detailed technical information and configuration of the element, refer to our [technical documentation](xref:Connector_help_WBD_SOT_Technical).
