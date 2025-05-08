---
uid: Connector_help_Grass_Valley_AMPP_Manager
---

# Grass Valley AMPP Manager

## About

![Gvampp_header.png](~/connector/images/Gvampp_header.png)

The Grass Valley Agile Media Processing Platform (GVAMPP) Solution integrates AMPP's robust processing capabilities into DataMiner, enabling its users to monitor and control various applications with exceptional efficiency.

The AMPP Manager is equipped with the essential functionality to list fabrics, nodes, and workloads. It also offers the ability to start or stop application instances, enabling advanced orchestration workflows.

### Key Features

- **Workloads**: Presents a detailed list of all existing workloads. Each instance includes the application, package, status, and dedicated action buttons, allowing users to efficiently manage operations.
- **Fabrics and Nodes**: Shows the collected fabrics, their nodes, and the relations between them.
- **Snapshots**: Displays a table listing all available snapshots, including relevant information about associated workloads. The interface also provides action buttons, allowing users to start or stop them as needed. This functionality helps facilitate the management of workload instances and their corresponding workloads.

> [!NOTE]
> Supported through the Workloads representation, productions offer a modern alternative to traditional snapshots. This approach allows users to manage production environments with the ability to start or stop workloads directly associated with a specific production.

## Use Cases

### Status Monitoring and Proactive Reaction

![Gvampp_workloads_error.png](~/connector/images/Gvampp_workloads_error.png)

**Challenge**: Daily workflows often necessitate a substantial number of workloads to function effectively. However, several factors can impact the availability of these instances, potentially rendering them unusable during critical operations, disrupting the processes and hindering the overall performance.

**Solution**: The **AMPP Manager** can periodically retrieve the workloads, exposing their status and serving as a source to create alarms or proactively react through DataMiner Correlation, which can range from delivering early pertinent notifications to implementing sophisticated recovering mechanisms by triggering restarts via Automation.

**Benefit**: The effectiveness of the workflows is ensured through the timely detection of workload errors, with even a potential automatic recovery.

### Reduction in Resource Costs

![Gvampp_snapshot_control.png](~/connector/images/Gvampp_snapshot_control.png)

**Challenge**: Whether in the cloud or on the ground, workloads incur costs that typically depend on how long the instances remain active. While AMPP offers a variety of excellent tools to calculate and track these expenses, it is still necessary to implement mechanisms associated with scheduled events. This way, workloads will only be active during the required times.

**Solution**: The **AMPP Manager** offers three different options for activating or deactivating workloads. These options include managing individual instances, using groups of pre-assigned workloads known as snapshots, or adopting the more modern approach of productions. Additionally, these alternatives can be integrated with MediaOps, enhancing not only configuration capabilities but also providing an effective means of cost control.

**Benefit**: Reducing the usage costs can lead to higher profitability and a smaller environmental footprint.

## Technical Info

### Prerequisites

- **DataMiner version 10.2 or higher**
- **SignalR Forwarder 3.4 or higher**

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Grass_Valley_AMPP_Manager_Technical).
