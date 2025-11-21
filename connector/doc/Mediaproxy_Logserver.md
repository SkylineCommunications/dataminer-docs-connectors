---
uid: Connector_help_Mediaproxy_Logserver
---

# Mediaproxy Logserver

The Mediaproxy Logserver connector enables comprehensive monitoring and control of the Mediaproxy Logserver platform. Through its integration with SNMP, REST API, and Push API, this connector provides complete visibility into system status, channels, and event-driven notifications, allowing operators to manage compliance logging environments efficiently and reliably from within DataMiner.

## Key Features

- **Real-time status monitoring**: Displays live information about the system, channels, and extracts while automatically updating alarm conditions and health indicators based on traps and event messages.

- **Event and extract integration**: Retrieves and displays event types, subtypes, and extracts directly from the REST and Push APIs, ensuring operators can easily track system events and content extraction processes.

## Use Cases

### Unified Compliance Monitoring

**Challenge**: Broadcasters operating multiple Logserver instances need a unified platform to supervise compliance logging, event activity, and system alerts across all devices.

**Solution**: The DataMiner connector consolidates data from SNMP traps, REST API polling, and Push API feeds into a single view, enabling operators to track channel health and system performance in real time.

**Benefit**: Centralized compliance monitoring with real-time alerts ensures operational consistency and faster incident resolution across distributed logging environments.

### Real-Time Event Intelligence

**Challenge**: Operators require instant awareness of critical broadcast events such as SCTE-35 triggers, caption failures, or transport interruptions.

**Solution**: The connector’s Push API and event pages provide immediate updates from incoming event messages, automatically mapping them to DataMiner alarms.

**Benefit**: Allows proactive detection and response to on-air issues, improving service reliability and reducing downtime during live broadcasts.

### Streamlined Maintenance and Troubleshooting

**Challenge**: Identifying and recovering from network or device issues across multiple channels and transport streams can be time-consuming.

**Solution**: The connector’s system and channel status pages highlight any service degradation, license warnings, or proxy accessibility issues, while offering reset controls to restore default values quickly.

**Benefit**: Simplifies root cause analysis and ensures faster recovery through actionable system insights and built-in reset functionality.

## Technical info

> [!NOTE]
> For more information on how to configure and use the DataMiner connector for Mediaproxy Logserver, refer to the [Technical help page](xref:Connector_help_Mediaproxy_Logserver_Technical).
