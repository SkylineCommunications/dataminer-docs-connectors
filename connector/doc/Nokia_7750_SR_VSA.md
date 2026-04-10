---
uid: Connector_help_Nokia_7750_SR_VSA
---

# Nokia 7750 SR VSA Connector

## About

The Nokia 7750 SR VSA connector provides monitoring capabilities for Video Service Assurance (VSA) functions on Nokia 7750 SR platforms. It enables visibility into video delivery performance by collecting TMNX Video Group parameters through SNMP.

The connector focuses on video-related metrics and infrastructure, allowing operators to monitor streaming behavior and system performance associated with v-ISA deployments.

---

## Key Features

- **Video Service Monitoring**: Tracks performance of video delivery services.
- **TMNX VDO GRP Visibility**: Displays structured data across video group tables.
- **Source Statistics Analysis**: Provides insights into video stream performance.
- **Hardware Monitoring**: Includes visibility into MDA processing components.
- **SNMP-Based Integration**: Simple deployment using standard SNMP connectivity.

---

## Use Cases

### Use Case 1  
**Challenge:** Monitoring video streaming performance in real time.  
**Solution:** Use the connector to track TMNX VDO GRP SRC statistics and identify performance issues.  
**Benefit:** Enables faster detection of degradation in video delivery.

### Use Case 2  
**Challenge:** Understanding infrastructure behavior for video services.  
**Solution:** Monitor MDA and video group data through dedicated tables.  
**Benefit:** Improves visibility into processing resources and service behavior.

### Use Case 3  
**Challenge:** Validating video service configurations and operation.  
**Solution:** Use the TMNX VDO GRP table to review configured video groups.  
**Benefit:** Ensures correct deployment and operation of video services.

---

## Technical Requirements

- Nokia 7750 SR device with VSA (v-ISA) functionality enabled.
- SNMP access configured with valid credentials.
- ESA infrastructure deployed for video processing.

> [!NOTE]  
> For detailed technical information, refer to our  
> **technical documentation** (xref:Connector_help_Nokia_7750_SR_VSA_Technical).