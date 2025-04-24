---
uid: Connector_help_Hughes_Pulse_Platform_VSAT
---

# Hughes Pulse Platform VSAT

## About

The **Hughes Pulse Platform VSAT** connector enables real-time monitoring of VSAT terminals using the Hughes Pulse API. It provides full visibility into terminal configuration, device status, and key performance metrics, making it ideal for network teams, NOC operators, and service providers managing large satellite networks.

## Key Features

**Centralized Remote Terminal Monitoring**  
Easily track the health and status of VSAT terminals in real time, from a single interface.

**End-to-End Network Performance Metrics**  
Continuously monitor ICMP latency, jitter, packet loss, signal quality (RSRP, RSSI, SINR), and throughput per terminal.

**Secure & Scalable API Integration**  
Built on secure REST API connections, ensuring reliable data access across large deployments.

**Terminal Configuration Insights**  
Gain immediate access to detailed terminal setup info, including ID, access mode, location, and current status.

## Use Cases

### Use Case 1  
**Challenge:** Network operations teams need a consolidated view of terminal performance across hundreds or thousands of remote VSAT sites.  
**Solution:** The connector centralizes device data and metrics in DataMiner, providing at-a-glance insight into status and performance.  
**Benefit:** Quicker root cause analysis, reduced mean time to resolution (MTTR), and fewer escalations.

### Use Case 2  
**Challenge:** NOC teams struggle to detect and react to network degradations in time.  
**Solution:** By polling metrics like latency, jitter, and signal quality at frequent intervals, the connector enables proactive monitoring.  
**Benefit:** Teams can set up DataMiner alarms and trending for early anomaly detection and service assurance.

## Technical Reference

### Prerequisites

- A valid Hughes Pulse API account with access to required endpoints.
- DataMiner System version 10.3.0 or higher.
- Connectivity to `https://api.hugheson.net` via HTTPS (port 443).

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:onnector_help_Hughes_Pulse_Platform_VSAT_Technical).