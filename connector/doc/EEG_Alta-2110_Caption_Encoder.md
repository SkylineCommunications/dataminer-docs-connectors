---
uid: Connector_help_EEG_Alta-2110_Caption_Encoder
---

# EEG Alta-2110 Caption Encoder

## About

The EEG Alta-2110 connector allows for the comprehensive monitoring and management of the EEG Alta-2110 captioning system. This solution is specifically designed to integrate with the SMPTE 2110 suite of standards, bridging the gap between cloud-based captioning services and local IP-based video production environments. By interfacing with the iCap Alta software via HTTP, this connector provides a centralized window into virtualized captioning workflows.

## Key Features

- **Virtualized SMPTE 2110 Integration**: Seamlessly monitor software-defined captioning tailored for 2110-30 (audio) and 2110-40 (ancillary) media streams.

- **Automated NMOS Support**: Full visibility and control over NMOS IS-04 and IS-05 protocols for automatic registration and connection management of media streams.

- **Dynamic Instance Management**: Easily create, edit, and track multiple encoder instances, each with unique stream, iCap, and Telnet settings.

- **Flexible Output Formatting**: Switch between SMPTE 334 CEA-708 VANC and OP 47 EBU Teletext packets to meet diverse regional broadcasting requirements.

- **Comprehensive Health Monitoring**: Track real-time iCap connection status, PTP grandmaster synchronization, and detailed logging for every encoder instance.

## Use Cases

### IP-Based Closed Captioning Workflow

**Challenge**: Transitioning from traditional SDI hardware to an IP-centric SMPTE 2110 environment while maintaining reliable closed captioning.

**Solution**: The EEG Alta-2110 connector integrates the virtualized encoder into the management platform, allowing operators to route 2110-40 ancillary data and manage cloud-based captioning through a single interface.

**Benefit**: Reduces physical hardware footprint and simplifies the transition to ST 2110 infrastructure.

### Multi-Language International Broadcasting

**Challenge**: Managing different captioning standards (CEA-708 vs. OP 47) and multiple languages across various global regions.

**Solution**: Use the connector to configure DVB Text settings and toggle output formats per instance, supporting up to 6 language services and specific Teletext magazine/page numbers.

**Benefit**: Streamlines global content distribution by allowing rapid reconfiguration of output standards via software.

### Legacy Bridge Integration

**Challenge**: The need to synchronize modern IP-based captioning data with legacy SDI encoders or older downstream devices.

**Solution**: Leverage the Telnet Settings management to clone "CTRL+A" style caption data from an iCap IP connection and route it to legacy hardware.

**Benefit**: Protects existing investments in SDI hardware while modernizing the core captioning workflow.

## Technical Reference

### Prerequisites

- **iCap Alta Virtual Machine** must be deployed on a supported host (VirtualBox, Cisco, or Microsoft Hyper-V).
- **Network Connectivity** between the system and the Alta VM via HTTP (Default Port 80).
- **iCap Account Credentials** (Company, Username, Password) are required for cloud-based captioning functionality.
- **SMPTE 2059 PTP Grandmaster** is recommended for accurate video frame rate interpretation and VITC timecode generation.

> [!NOTE]
> For detailed technical information regarding parameter IDs, polling cycles, and specific configuration steps, refer to our [technical documentation](xref:Connector_help_EEG_Alta-2110_Caption_Encoder_Technical).
