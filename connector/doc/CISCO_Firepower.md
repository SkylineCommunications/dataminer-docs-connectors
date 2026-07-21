---
uid: Connector_help_CISCO_Firepower
---

# CISCO Firepower

## About

This connector uses SNMP or HTTP communication in order to monitor a CISCO Firepower device. It retrieves fan statistics, monitor statistics, power supply statistics, and more. It also provides an overview of how all these components are behaving, and it displays the average, maximum, and minimum values for specific parameters such as the fan speed and the motherboard input and output current.

![Interfaces](~/connector/images/Cisco_Firepower.png)

## Key Features

- **Network interface monitoring**:

  - Real-time tracking of interface bit rates and bandwidth utilization.
  - Octet and packet statistics for detailed traffic analysis.
  - Per-interface performance visibility.

- **Hardware health monitoring**:

  - Fan operation statistics, speed measurements, and status tracking.
  - Power supply monitoring with voltage and current measurements.
  - Temperature and thermal management system oversight.

- **Alert and threshold management**:

  - Customizable alert configuration.
  - Threshold-based monitoring and notifications.

## Use Cases

### Interface and Throughput Health Monitoring

**Challenge**: Firepower devices often act as critical traffic choke points, where performance degradation directly affects services.

**Solution**: The connector tracks interface status, throughput, errors, drops, CPU, memory, and failover state.

**Benefit**: Improves service reliability by correlating firewall performance with upstream and downstream network elements and supporting SLA monitoring.

### VPN Health – Site-to-Site and Remote Access

**Challenge**: VPN failures can disrupt entire sites or remote users without immediate visibility into the root cause.

**Solution**: The connector monitors tunnel states, negotiation failures, rekey events, and remote access user counts.

**Benefit**: Enables rapid correlation between VPN issues and service outages, while providing historical insights for capacity planning.

### Security Posture and Threat Visibility

**Challenge**: Security events are scattered across Firepower dashboards, making it difficult to correlate threats with network or service impact.

**Solution**: The connector centralizes intrusion counters, blocked connections, threat statistics, and top talkers, correlating Firepower security telemetry with network and service data.

**Benefit**: Provides single-pane-of-glass visibility, enabling faster root cause analysis and targeted alarms when security events impact service quality.

### Firewall and NAT Session Capacity Monitoring

**Challenge**: Firewall and NAT session tables can silently approach capacity, leading to sudden service outages.

**Solution**: The connector continuously monitors active sessions, session rates, NAT translations, and peak utilization.

**Benefit**: Enables proactive alarms, capacity forecasting, and data-driven decisions on when to scale or upgrade firewall infrastructure.

## Technical Reference

> [!NOTE]
> For setup and configuration instructions, refer to the [technical documentation](xref:Connector_help_CISCO_Firepower_Technical).
