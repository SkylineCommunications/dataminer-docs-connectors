---
uid: Connector_help_HP_Synergy
---

# HP Synergy

## About

HP Synergy is a composable infrastructure platform that enables IT teams to provision and manage compute, storage, and network resources through the HP OneView management platform. This DataMiner connector integrates HP Synergy into DataMiner via the HP OneView RESTful API, giving operators centralized visibility across all physical and logical resources within the Synergy frame.

## Key Features

- **Composable infrastructure overview**: Monitor enclosures, enclosure groups, and logical enclosures alongside the device bays, fan bays, power supply bays, and manager bays they contain.

- **Server lifecycle visibility**: Track server hardware, server hardware types, server profiles, and server profile templates from a single DataMiner element.

- **Network resource monitoring**: Get a unified view of connections, connection templates, Ethernet networks, FC networks, FCoE networks, fabrics, and network sets.

- **Interconnect topology**: Monitor interconnects, logical interconnects, uplink sets, uplink ports, and logical interconnect groups to understand the full switching fabric.

- **Storage management**: Track storage systems, storage pools, storage volumes, storage volume sets, managed SANs, SAN volume attachments, and server profile storage configurations.

- **Alerts and task tracking**: Monitor active alerts, events, and operational tasks — with configurable task filters — to stay on top of infrastructure changes and incidents.

## Use Cases

### Centralized Composable Infrastructure Management

**Challenge**: Large data centers running HP Synergy need a single pane of glass to track the health and configuration of hundreds of compute, network, and storage resources spread across multiple enclosures and frames.

**Solution**: The HP Synergy connector pulls all resource data from the HP OneView API into DataMiner, making enclosures, servers, networks, storage, and facilities available in one consolidated view with trending and alarm monitoring.

**Benefit**: Reduced mean time to detect (MTTD) infrastructure issues, fewer manual checks, and a consistent operational overview regardless of the number of Synergy frames deployed.

### Proactive Hardware Health Monitoring

**Challenge**: Hardware faults in blade servers, drive enclosures, or power supplies can go unnoticed until they cause service-impacting outages.

**Solution**: The connector continuously polls the HP OneView API for device bay status, drive enclosure health, power supply bay information, and appliance health data. DataMiner alarm thresholds and trending surface degradation trends before they escalate.

**Benefit**: Earlier detection of hardware issues, faster response times, and reduced risk of unplanned downtime caused by undetected component failures.

### Server Profile Compliance and Change Tracking

**Challenge**: In composable environments, server profiles and their associated network and storage configurations change frequently. Tracking what is deployed where — and detecting unauthorized changes — is difficult without automated tooling.

**Solution**: The connector monitors server profiles, server profile templates, and server profile storage configurations (local storage controllers, logical drives, logical JBODs, and SAN volume attachments). DataMiner can trigger alerts when profile configurations drift from expected templates.

**Benefit**: Improved configuration governance, faster change auditing, and reduced risk of misconfigured server profiles causing network or storage connectivity issues.

## Technical Reference

### Prerequisites

- **DataMiner version 10.4.0.0 (build 14003) or higher** is required.

- **HP OneView credentials** (username, password, and domain) must be available and entered on the **General** page after element creation before polling can start.

- **HTTP network connectivity** between the DataMiner Agent and the HP OneView management platform on the configured IP and port is required.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_HP_Synergy_Technical).
