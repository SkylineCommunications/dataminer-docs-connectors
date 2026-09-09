---
uid: Connector_help_ScheduAll_Generic_Interop_Manager
---

# ScheduAll Generic Interop Manager

## About

The **ScheduAll Generic Interop Manager** connector integrates DataMiner with the ScheduAll Interop Listener web service.
It logs in to ScheduAll over HTTP, keeps the session alive, and exchanges work order and booking information between ScheduAll and other systems, allowing scheduling data to be automated and orchestrated directly from DataMiner.

## Key Features

- **Interop session management**: Automatically logs in to and out of the ScheduAll Interop Listener, keeps track of the session cookie, and continuously validates the login status so the connection stays available.

- **Live work order tracking**: Maintains a Work Orders table with instance, chain, start/end time, message type, booking status, and custom field data, and automatically cleans up expired work orders.

- **Message buffering and orchestration**: Buffers incoming and outgoing interop and booking messages, and triggers a configurable Orchestration Script once a maximum number of messages or a maximum wait time is reached.

- **Configurable field mapping**: Offers a Field Mapping table that lets users map ScheduAll custom tags to specific columns, allowing the connector to be adapted to different downstream data models without code changes.

- **InterApp command support**: Exposes InterApp Receiver/Return parameters so other DataMiner elements or Automation scripts can send interop commands to ScheduAll and receive responses programmatically.

## Use Cases

### Automated Booking Orchestration

**Challenge**: Confirming and acting on ScheduAll bookings manually slows down resource allocation for media operations.

**Solution**: The connector receives interop and booking messages from ScheduAll and buffers them until a configured threshold or wait time is reached, then triggers an Orchestration Script to act on them automatically.

**Benefit**: Faster response to new or changed bookings, less manual intervention, and fewer missed updates.

### Centralized Scheduling Visibility

**Challenge**: Operations teams need a single place to see the status of ScheduAll work orders without opening the ScheduAll application itself.

**Solution**: The connector's Work Orders table surfaces booking status, start/end times, message type, and custom fields in real time within DataMiner.

**Benefit**: Unified, real-time visibility into scheduling data alongside other monitored systems.

### Flexible Integration with Downstream Systems

**Challenge**: ScheduAll custom tags don't always line up with the fields expected by other systems that need the booking data.

**Solution**: The Field Mapping table lets users map ScheduAll custom tags to the columns required by downstream integrations, and InterApp calls expose this data to other DataMiner elements or scripts.

**Benefit**: The connector can be adapted to new integrations purely through configuration, without requiring driver changes.

## Technical Reference

### Prerequisites

- **Network access to the ScheduAll Interop Listener web service** is needed so the connector can log in, send commands, and receive responses over HTTP.

- **A valid ScheduAll interop user name and password** are needed for the connector to authenticate and maintain a login session.

- **DataMiner 10.3.0.0 (build 12752) or higher** is required to run this connector.
