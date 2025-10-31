---
uid: Connector_help_SES_Service_Problem_Management
---

# SES Service Problem Management

## About

The SES Service Problem Management connector provides integration between DataMiner ticketing module and SNOW system, enabling automated ticket lifecycle management and bidirectional synchronization. Based on the TMF656 Service Problem Management API standard, this connector transforms DataMiner tickets into service problems, ensuring reliable incident tracking and resolution across the entire infrastructure.

## Key Features

- **Automated Ticket Synchronization**: Bidirectional synchronization between DataMiner Ticketing System and SES Service Problem Management with configurable frequency (10 seconds to 24 hours).

- **Complete Lifecycle Management**: Automatically creates, updates, and closes service problems based on DataMiner ticket state changes, ensuring accurate incident tracking throughout the entire resolution process.

- **Multi-Threaded Performance**: Utilizes 5 concurrent processing threads for efficient ticket creation and updates, enabling high-volume ticket management without performance degradation.

- **Event Problem Creation**: Automatically generates event-level problems for device alarms, providing detailed correlation between infrastructure events and service-level impacts.

- **Real-Time Monitoring**: Live tracking of managed tickets with visibility into synchronization status, frequency, and ticket counts through an intuitive interface.

## Use Cases

### Use Case 1

**Challenge**: Network operations teams struggle to maintain consistent incident tracking between DataMiner's alarm management and enterprise service management systems, leading to lost tickets, duplicate work, and delayed resolution times.

**Solution**: The connector automatically synchronizes DataMiner tickets with SES Service Problem Management in real-time, creating service problems for new tickets, updating them as ticket states change, and closing them when issues are resolved.

**Benefit**: Operations teams achieve 100% ticket visibility across both systems, eliminating manual ticket entry, reducing resolution time by up to 40%, and ensuring no incidents fall through the cracks.

### Use Case 2

**Challenge**: Service providers need to correlate device-level alarms with service-level impacts to provide customers with accurate incident notifications and SLA reporting.

**Solution**: The connector creates both service problems (for service-level tickets) and event problems (for device-level alarms), establishing clear relationships between infrastructure issues and affected services.

**Benefit**: Organizations gain complete end-to-end visibility from infrastructure alarms to customer service impacts, enabling proactive customer communication and accurate SLA compliance reporting.

### Use Case 3

**Challenge**: High-volume network operations environments experience bottlenecks when synchronizing hundreds of tickets between systems, causing delays in incident response and system performance issues.

**Solution**: The connector leverages multi-threaded architecture with 5 parallel processing threads and configurable synchronization intervals, efficiently handling large ticket volumes without impacting system performance.

**Benefit**: Operations teams can process up to 5 times more tickets simultaneously, reducing synchronization latency from minutes to seconds and maintaining system responsiveness even during major incident events.

## Technical Reference

### Prerequisites

- **DataMiner Ticketing License** is required for the connector to access and manage tickets through the DataMiner Ticketing Gateway.

- **Network Connectivity** to the SNOW API endpoint over HTTPS (port 443) is needed for bidirectional communication.

- **Authentication Credentials** (username and password) with appropriate permissions to create, read, and update service problems in the SES system are required for API access.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_SES_Service_Problem_Management_Technical).
