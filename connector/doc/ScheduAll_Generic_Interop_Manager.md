---
uid: Connector_help_ScheduAll_Generic_Interop_Manager
---

# ScheduAll Generic Interop Manager

## About

The **ScheduAll Generic Interop Manager** connector integrates DataMiner with the ScheduAll Interop Listener web service.

It logs in to ScheduAll over HTTP, keeps the session alive, and exchanges work order and booking information between ScheduAll and other systems, allowing scheduling data to be automated and orchestrated directly from DataMiner.

## Key Features

- **Keep your integration reliably connected**: Automatically maintain a live connection to ScheduAll, so scheduling data keeps flowing without manual intervention.

- **Track bookings in real time**: Follow work orders as they progress, giving your team an always up-to-date view of scheduling activity.

- **Automate your response to booking changes**: Trigger downstream actions automatically once new or updated bookings come in, speeding up resource allocation.

- **Connect scheduling to the rest of your workflow**: Let other DataMiner elements and Automation scripts send commands to and receive responses from ScheduAll.

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

- **A valid ScheduAll interop username and password** are needed for the connector to authenticate and maintain a login session.

- **DataMiner 10.3.0.0 - 12752 or higher** is required to run this connector.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_ScheduAll_Generic_Interop_Manager_Technical).
