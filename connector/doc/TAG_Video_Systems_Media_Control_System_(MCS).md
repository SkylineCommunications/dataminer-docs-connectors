---
uid: Connector_help_TAG_Video_Systems_Media_Control_System_MCS
---

# TAG Video Systems Media Control System (MCS)

## About

The **TAG Video Systems Media Control System (MCS) connector** provides HTTP-based integration between DataMiner and TAG's Media Control System. It enables DataMiner to monitor, configure, and control the MCS platform via its REST API, aggregating data and exposing alarms and media health metrics within DataMiner dashboards.

> [!NOTE]
> This connector is bundled with the TAG MCM-9000 connector in the **TAG Management** application. For more information, see [TAG Management](https://catalog.dataminer.services/details/0ef8f78a-beeb-4ec0-b321-e79b26b393ce)

## Key Features

- **HTTP/REST connectivity**: Communicates with MCS via HTTP REST API, enabling seamless two-way control and status updates.
- **Event-driven updates via SNMP traps**: Listens on port 162 for automatic updates when MCS events occur.
- **Data aggregation & orchestration**: Collects and correlates media health and performance data across all TAG MCM devices.
- **Unified visualization & automation**: Integrates MCS metrics, alarms, and control into DataMiner dashboards and low-code apps for unified monitoring and orchestration.

## Use Cases

### Use Case 1

**Challenge**: Operators lacked a unified view of media health and infrastructure status across TAG and DataMiner platforms.

**Solution**: Use the MCS connector to bring TAG MCS data, alarms, and controls into DataMiner dashboards and apps.

**Benefit**: Real-time insights into both content health and infrastructure, streamlined workflows, and improved operational efficiency.

### Use Case 2

**Challenge**: Scaling TAG deployments across multiple MCM elements and MCS clusters required complex configuration.

**Solution**: The MCS connector serves as a single integration point, simplifying deployment through automated discovery and control logic.

**Benefit**: Faster rollout and simplified management of large TAG ecosystems with reduced configuration overhead.

### Use Case 3

**Challenge**: Media anomalies and failures were buried in log files, with delayed troubleshooting.

**Solution**: The connector surfaces MCS-aggregated media health metrics and alarms into DataMiner, enabling proactive dashboards and alerts.

**Benefit**: Faster root cause identification, proactive fault detection, and improved viewer experience.

## Technical Reference

### Prerequisites

- **DataMiner version 10.4.3 or higher** is required for full MCS connector functionality.
- **Credentials for MCS**: A valid username and password are needed for HTTP-based authentication.

> [!NOTE]
> For detailed technical information about the connector, refer to our [technical documentation](https://docs.dataminer.services/connector/doc/TAG_Video_Systems_Media_Control_System_(MCS)_Technical.html).
