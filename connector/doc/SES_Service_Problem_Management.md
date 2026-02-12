---
uid: Connector_help_SES_Service_Problem_Management
---

# SES Service Problem Management

## About

The SES Service Problem Management connector integrates the DataMiner SDM Ticketing module with the SNOW system, enabling automated ticket lifecycle management and bidirectional synchronization. Based on the TMF656 Service Problem Management API standard, this connector transforms DataMiner tickets into service problems, ensuring reliable incident tracking and resolution across the entire infrastructure.

## Key Features

- **Automated ticket synchronization**: Bidirectional synchronization between the DataMiner SDM Ticketing system and SES Service Problem Management with configurable frequency (10 seconds to 24 hours).

- **Complete lifecycle management**: Automatically creates, updates, and closes service problems based on DataMiner ticket state changes, ensuring accurate incident tracking throughout the resolution process.

- **Multithreaded performance**: Utilizes 5 concurrent processing threads for efficient ticket creation and updates, enabling high-volume ticket management without performance degradation.

- **Event problem creation**: Automatically generates event-level problems for device alarms, providing detailed correlation between infrastructure events and service-level impact.

- **Real-time monitoring**: Live tracking of managed tickets with visibility on synchronization status, frequency, and ticket counts through an intuitive interface.

## Use Cases

### Real-Time Synchronization with Ticketing System

**Challenge**: Network operations teams struggle to maintain consistent incident tracking between DataMiner's alarm management and enterprise service management systems, leading to lost tickets, duplicate work, and delayed resolution times.

**Solution**: The connector automatically synchronizes DataMiner tickets with SES Service Problem Management in real time, creating service problems for new tickets, updating them as ticket states change, and closing them when issues are resolved.

**Benefit**: Operations teams achieve 100% ticket visibility across both systems, eliminating manual ticket entry, reducing resolution time by up to 40%, and ensuring no incidents fall through the cracks.

### Immediate Insight in Service Impact

**Challenge**: Service providers need to correlate device-level alarms with service-level impact to provide customers with accurate incident notifications and SLA reporting.

**Solution**: The connector creates both service problems (for service-level tickets) and event problems (for device-level alarms), establishing clear relationships between infrastructure issues and affected services.

**Benefit**: Organizations gain complete end-to-end visibility, from infrastructure alarms to customer service impact, enabling proactive customer communication and accurate SLA compliance reporting.

### Processing of High Volumes of Tickets

**Challenge**: High-volume network operations environments experience bottlenecks when synchronizing hundreds of tickets between systems, causing delays in incident response and system performance issues.

**Solution**: The connector leverages multithreaded architecture with five parallel processing threads and configurable synchronization intervals, efficiently handling large ticket volumes without impacting system performance.

**Benefit**: Operations teams can process up to five times more tickets simultaneously, reducing synchronization latency from minutes to seconds and maintaining system responsiveness even during major incident events.

## Prerequisites

This connector requires **DataMiner 10.5.0** or higher because of dependencies on:

- SDM Ticketing APIs (`TicketingApiHelper`).
- The **DataMiner SDM Ticketing** solution must be available on the DataMiner system.
- **Authentication credentials** (username and password) with appropriate permissions to create, read, and update service problems in the SES system are required for API access.

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_SES_Service_Problem_Management_Technical).
