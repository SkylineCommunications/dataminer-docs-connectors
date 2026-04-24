---
uid: Connector_help_EVS_IPD-VIA
---

# EVS IPD-VIA

## About

**EVS IPD-VIA** is the web-based asset management component of EVS's VIA ecosystem, enabling access to, management, editing, and sharing of live production assets. The EVS IPD-VIA connector integrates DataMiner with the EVS OpenGate v2 API and RabbitMQ message queues, giving operators a centralized view of recording sessions and enabling automated recording workflow orchestration from within the DataMiner ecosystem.

## Key Features

- **Live recording session monitoring**: Track all ongoing and scheduled recording sessions in real time, with immediate updates delivered via RabbitMQ subscriptions, without polling delay.
- **Full recording session lifecycle management**: Create, update, and delete recording sessions programmatically through the DataMiner InterApp framework, using the `Skyline.DataMiner.ConnectorAPI.EVS.IPD-VIA` NuGet package.
- **Recorder and target discovery**: Automatically retrieve all available recorders and targets from the EVS system, keeping the connector's reference data in sync with the platform.
- **Metadata and profile support**: Retrieve and display recording session metadata, profiles, and profile fields, enabling rich context for each session.
- **Configurable session retention**: Define how long completed recording sessions are kept in DataMiner before automatic removal, reducing clutter without losing operational visibility.

## Use Cases

### No Unified View of Recording Activity

**Challenge**: In a busy live production environment, recording sessions span multiple recorders and targets. Without a central view, operators must check the EVS platform directly to understand what is recording, what is scheduled, and what has failed.

**Solution**: DataMiner aggregates all recording sessions from EVS IPD-VIA into a single table, continuously updated via RabbitMQ. Operators get an instant, unified overview of every active and scheduled session across the entire EVS infrastructure, without leaving the DataMiner interface.

### Reactive Instead of Proactive Fault Management

**Challenge**: Recording failures or unexpected status changes in EVS IPD-VIA are only discovered after the fact, when content is found to be missing or incomplete.

**Solution**: DataMiner's alarm and trending engine monitors recording session statuses in real time. Operators can configure alarms on session state changes (for example, when a session moves to *InError*), enabling proactive intervention before content loss occurs.

### Manual, Script-Driven Recording Orchestration

**Challenge**: Scheduling and managing recording sessions requires direct interaction with the EVS platform, making it difficult to integrate recording workflows into broader automation pipelines.

**Solution**: Through the InterApp framework, any DataMiner automation script can send create, update, and delete requests to the connector, which translates them into the correct OpenGate v2 API calls. This allows recording orchestration to be embedded in larger broadcast workflows, such as live event rundowns or ingest pipelines, without manual operator steps.

### Difficulty Correlating Recording Issues with Infrastructure Problems

**Challenge**: When a recording session fails, it is not immediately clear whether the cause is an EVS platform issue, a network problem, or a configuration error elsewhere in the infrastructure.

**Solution**: DataMiner's cross-domain correlation engine can link recording session alarms from EVS IPD-VIA with alerts from network devices, servers, and other broadcast systems. This gives operators root-cause visibility across the full infrastructure stack, speeding up diagnosis and resolution.

## Technical Reference

### Prerequisites

- EVS VIA MAP **1.1** or higher (OpenGate API v2).
- RabbitMQ **3.8.5** or higher.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_EVS_IPD-VIA_Technical).
