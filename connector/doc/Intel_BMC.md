---
uid: Connector_help_Intel_BMC
---

# Intel BMC

## About

The **Intel Baseboard Management Controller (BMC)** is a built-in server management chip that lets you monitor, control, and troubleshoot systems remotely — even if the OS is down.

**Unlock smarter server management with the Intel BMC Connector.**
Seamlessly integrate with Intel® Server Systems and leverage the power of the OpenBMC Redfish* API to monitor, control, and automate your infrastructure. From hardware health checks to power, thermal, and system insights, the Intel BMC Connector gives you real-time visibility and remote management capabilities — all without stepping into the data center. Faster troubleshooting, less downtime, and smarter operations start here.

## Key Features

- **Remote System Management**: Monitor and control your server hardware without physical access, even when the operating system is offline.

- **OpenBMC Redfish API Support**: Industry-standard API interface for seamless integration with automation tools and third-party monitoring platforms.

- **Hardware Health Monitoring**: Real-time insights into CPU, memory, fans, storage, power supplies, and temperature sensors.

- **Power & Thermal Management**: Retrieve and control power usage, fan speeds, and thermal thresholds to optimize energy efficiency.

- **Event & Alert Handling**: Receive and process system events, alerts, and hardware status changes instantly.

- **Inventory & Configuration Access**: View detailed hardware inventory and adjust system settings remotely.

- **Secure Remote Access**: Built-in authentication and encrypted communication for safe server management.

- **Multi-System Support**: Manage multiple Intel® Server Systems through a single integration.

## Use Cases

### Remote Troubleshooting in Data Centers

**Challenge**:  A server in a remote data center becomes unresponsive, and on-site staff are unavailable to diagnose the issue.

**Solution**: The Intel BMC Connector provides out-of-band access via the Redfish API, allowing admins to view system logs, monitor hardware health, and perform a remote reboot.

**Benefit**: Eliminates the need for on-site visits, reduces downtime, and speeds up incident resolution.

### Automated Hardware Health Checks

**Challenge**: Large server farms require daily health monitoring to detect failures before they impact services.

**Solution**: The Intel BMC Connector integrates with automation scripts to query CPU temperatures, fan speeds, and power usage at regular intervals.

**Benefit**: Proactively detects hardware issues, reducing unplanned outages and improving service reliability.

### Energy Optimization in Cloud Environments

**Challenge**: High energy costs and thermal constraints in large-scale deployments.

**Solution**: The connector retrieves detailed power and thermal metrics via Redfish, enabling automated cooling and power usage adjustments.

**Benefit**: Optimizes energy efficiency, lowers operational costs, and extends hardware lifespan.

### Asset Inventory and Compliance Auditing

**Challenge**: IT teams struggle to keep hardware inventory data up to date across multiple locations.

**Solution**: The Intel BMC Connector collects inventory information (CPU, memory, firmware versions, etc.) automatically via API.

**Benefit**: Saves time on manual audits, ensures compliance, and improves asset tracking accuracy.

## Technical Reference

### Prerequisites

- **Valid BMC User Account with correct login credentials** is required to access the Redfish API and retrieve system data.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Intel_BMC_Technical).
