---
uid: Connector_help_Xiplink_XA100K
---

# Xiplink XA100K

## About

The Xiplink XA100K connector provides monitoring of SCPS-based satellite and WAN optimization appliances. It delivers visibility into system health, connection performance, CPU utilization, redundancy behavior, service status, and tunnel connectivity.

The connector consolidates operational and protocol-level performance metrics into a single DataMiner element, enabling effective monitoring of high-latency optimized network environments.

## Key Features

- **System Health Monitoring**: Track system description, uptime, OS version, and device identity information.

- **Connection Performance Monitoring**: Monitor SCPS and non-SCPS connection behavior, retransmission metrics, and congestion control statistics.

- **CPU Performance Tracking**: Observe CPU usage trends over 1, 5, and 15-minute intervals.

- **Service Monitoring**: Track service health, service count, and quality of service metrics.

- **Tunnel Visibility**: Monitor tunnel status, peer state, and uptime information.

- **Redundancy Awareness**: View redundancy and failover-related operational parameters.

## Use Cases

### Satellite Optimization Monitoring

**Challenge**: High-latency satellite links require continuous performance optimization visibility.

**Solution**: The connector exposes SCPS retransmission, congestion control, and recovery metrics.

**Benefit**: Improved link efficiency and reduced retransmission overhead.

### System Performance Monitoring

**Challenge**: Operators need visibility into system load and CPU behavior across optimization nodes.

**Solution**: The connector provides CPU trend statistics and system health indicators.

**Benefit**: Early detection of performance degradation.

### Service and Tunnel Stability

**Challenge**: Service degradation or tunnel instability can impact optimized traffic flows.

**Solution**: The connector monitors service status and tunnel connectivity state.

**Benefit**: Faster troubleshooting and improved service reliability.

## Technical Reference

### Prerequisites

- SNMP connectivity between DataMiner and the Xiplink XA100K device.
- Valid SNMP community string configured on the device.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Xiplink_XA100K_Technical).
