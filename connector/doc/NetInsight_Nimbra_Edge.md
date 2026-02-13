---
uid: Connector_help_NetInsight_Nimbra_Edge
---

# NetInsight Nimbra Edge

## About

The NetInsight Nimbra Edge connector for DataMiner provides full integration with the Nimbra Edge platform, enabling real-time monitoring, configuration, and orchestration of IP-based media workflows across distributed environments. This connector ensures operators have full visibility and control over all media delivery paths and services in cloud, hybrid, or on-premises deployments.

## Key Features

- **Full visibility of inputs and outputs**: Discover and monitor live streams across a variety of protocols including UDP, RTP, RTMP, RIST, ZIXI, and SRT.

- **Group assignment with ownership control**: Assign multiple groups to each input and flag ownership status directly from the UI.

- **Flow Engineering interface**: Visualize and manage the lifecycle of media flows using the Flow Logic Engine (FLE) integration.

- **Service and appliance monitoring**: Real-time retrieval of appliance, service, port, and region metadata via REST APIs.

- **Comprehensive metrics and alarms**: Includes TS metrics, TR 101 290 validation, and alarm collection with deduplication support.

- **Dynamic input/output provisioning**: Create, edit, or delete stream endpoints on the fly.

## Use Cases

### Centralized Monitoring of Distributed Stream Inputs

**Challenge**: A broadcaster has multiple ingest points across regions, each delivering live streams using different protocols. Monitoring them individually is complex and error-prone.

**Solution**: With the Nimbra Edge connector, all inputs are automatically discovered and displayed within the DataMiner interface. Operators can view real-time metrics, check input health (e.g. TR 101 290), and categorize them by region or type.

**Benefit**: One centralized view for all input streams, improving operational efficiency and reducing the time to identify faulty sources.

### Orchestrated Contribution-to-Distribution Workflow

**Challenge**: Managing transitions between incoming contribution feeds and outgoing distribution channels across multiple locations requires manual configuration, which is slow and error-prone.

**Solution**: Use the connector’s Flow Engineering interface to visualize and manage connections between incoming and outgoing flows. InterApp messaging ensures real-time updates and logic tracking.

**Benefit**: Streamlined flow control, less human error, and improved responsiveness during live broadcast operations.

### Multi-Tenant Input Access Control

**Challenge**: A service provider hosts streams for different customers, but needs a way to control which groups can access or own specific inputs.

**Solution**: Using the Group Assignment feature in the connector, operators can assign multiple groups to an input and specify ownership directly within the DataMiner UI.

**Benefit**: Secure and scalable multi-tenant support, ensuring each client only sees and controls their designated streams.

### Cloud-Native Stream Provisioning

**Challenge**: Provisioning or editing streams in a cloud-based media platform typically requires switching to the vendor's web interface, slowing down response times.

**Solution**: Operators can create, edit, or delete inputs and outputs directly within DataMiner using automation scripts or context menu actions powered by the Nimbra Edge connector.

**Benefit**: Faster provisioning, fewer tools to manage, and improved workflow automation.

## Technical info

> [!NOTE]
> For more information on how to configure and use the DataMiner connector for NetInsight Nimbra Edge, refer to the [Technical help page](xref:Connector_help_NetInsight_Nimbra_Edge_Technical).
