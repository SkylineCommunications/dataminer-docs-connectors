---
uid: Connector_help_Techex_Darwin_I-Frame_Switch
---

# Techex Darwin I-Frame Switch

## About

The **I-Frame Switch** module is a broadcast-grade source switcher that performs frame-accurate switching between I-frame-only video streams such as JPEG XS and I-frame-only H.264/HEVC, typically for redundancy, protection, and contribution workflows.

The **Techex Darwin I-Frame Switch** connector allows DataMiner to monitor and control Techex Darwin I-Frame Switch devices. This connector provides comprehensive monitoring of transport stream processing modules, including configuration management, input/output monitoring, and real-time statistics collection through both HTTP API polling and Kafka message subscriptions.

## Key Features

- **Comprehensive module management**: Monitor and manage multiple processing modules with granular control over polling states, configuration parameters, and operational status for each module instance.

- **Real-time Kafka integration**: Subscribe to Kafka topics for instant event streaming and statistics updates, enabling rapid response to changes in transport stream processing and immediate alerting on critical events.

- **Advanced input/output monitoring**: Track all input and output streams with detailed visibility into source information, PID (Program Identifier) values, video status, and timing data for comprehensive stream management.

- **Flexible configuration control**: Manage advanced module settings including Linux process priorities, scheduler priorities, core affinity assignments, and seamless switching timeouts to optimize performance for specific operational requirements.

## Use Cases

### Transport Stream Redundancy Management

**Challenge**: Broadcast operations require seamless failover between primary and backup transport streams without viewer-noticeable interruptions, while maintaining constant monitoring of both streams.

**Solution**: The connector provides real-time monitoring of input stream health, automatic switching capabilities with configurable timeout thresholds, and instant alerting through Kafka integration when stream quality degrades or sources fail.

**Benefit**: Minimizes service interruptions, reduces mean time to recovery (MTTR), and ensures continuous broadcast quality with automated failover mechanisms and comprehensive visibility into switching events.

### Multi-Module Performance Optimization

**Challenge**: Complex broadcast facilities operate multiple processing modules simultaneously, requiring fine-tuned resource allocation and priority management to prevent processing bottlenecks and ensure consistent output quality.

**Solution**: The connector exposes detailed configuration controls for Linux priorities, scheduler priorities, and CPU core affinity, allowing operators to optimize each module's performance characteristics based on workload requirements and system resources.

**Benefit**: Maximizes processing efficiency, reduces latency in critical paths, and enables data-driven capacity planning through comprehensive monitoring of module performance and resource utilization.

### Centralized Event Monitoring and Analytics

**Challenge**: Distributed transport stream processing infrastructure generates high volumes of events and statistics that need to be aggregated, correlated, and analyzed for operational insights and compliance reporting.

**Solution**: Kafka-based event streaming integration enables real-time data collection from all modules, centralized storage in DataMiner, and correlation with other broadcast infrastructure components for holistic operational visibility.

**Benefit**: Accelerates troubleshooting workflows, enables proactive maintenance through trend analysis, and provides comprehensive audit trails for compliance and quality assurance purposes.

## Prerequisites

- **Kafka broker configuration** is required for real-time event streaming integration.

- **DataMiner version 10.4.0.0 - 14003 or higher** is required for full compatibility with this connector's features.

## Technical Reference

> [!NOTE]
> For detailed technical information, configuration procedures, and page-by-page documentation, refer to our [technical documentation](xref:Connector_help_Techex_Darwin_I-Frame_Switch_Technical).
