---
uid: Connector_help_EEG_Alta-TS_Caption_Encoder
---

# EEG Alta-TS Caption Encoder

## About

This connector allows DataMiner to monitor and manage the EEG / AI-Media Alta-TS Caption Encoder.

Alta-TS is a software-based caption encoder designed for MPEG Transport Stream (MPEG-TS) workflows. It enables insertion, transport, and monitoring of closed captions and subtitles in IP video environments and can integrate with the AI-Media iCap cloud captioning platform. Alta-TS is typically deployed as a virtual machine.

The connector communicates with Alta-TS over HTTP(S) and provides visibility into encoder instances, stream configuration, captioning status, system alarms, logs, and operational statistics.

## Key Features

- **Centralized monitoring of Alta-TS encoder instances**: Provides visibility into all configured encoder instances, including operational status, instance configuration, and runtime information from a single DataMiner element.
- **Transport stream workflow monitoring**: Monitors MPEG-TS transport stream inputs and outputs, including RTP, UDP unicast, and UDP multicast stream configurations used by caption encoding workflows.
- **Caption workflow visibility**: Tracks caption insertion and caption bridging configurations to help operators verify that caption services are correctly configured and operational.
- **Operational logging and diagnostics**: Provides access to instance-specific logs and status information, enabling faster root cause analysis of stream, captioning, and service-related issues.
- **Configuration awareness across multiple channels**: Monitors key instance settings, including primary streams, source streams, and output destinations, allowing operators to validate channel configurations from a centralized platform.

## Use Cases

### Broadcast Captioning Service Assurance

**Challenge**: Broadcast operators need to ensure that caption encoding services remain operational across multiple transport stream channels while minimizing the risk of undetected caption failures.

**Solution**: The connector provides centralized monitoring of Alta-TS encoder instances, including channel status, caption configuration, and operational health.

**Benefit**: Operators can quickly detect service degradation, reduce downtime, and maintain compliance with captioning requirements.

### MPEG-TS Stream Monitoring

**Challenge**: Failures in transport stream inputs or outputs can disrupt caption delivery and impact downstream broadcast or OTT services.

**Solution**: The connector monitors stream configurations and operational status for RTP, UDP unicast, and UDP multicast workflows configured on Alta-TS instances.

**Benefit**: Operations teams gain immediate visibility into failing or misconfigured streams, accelerating fault isolation and resolution.

### Multi-Channel Encoder Management

**Challenge**: Managing multiple caption encoding channels through individual web interfaces becomes increasingly complex and time-consuming.

**Solution**: The connector aggregates information from all configured Alta-TS instances into a single DataMiner view, including status, configuration, and logs.

**Benefit**: Operators can monitor and troubleshoot multiple channels from a centralized operational platform, improving efficiency and reducing operational overhead.

### Faster Incident Troubleshooting

**Challenge**: When caption delivery problems occur, engineers need quick access to diagnostic information to identify the root cause.

**Solution**: The connector exposes operational logs and instance health information directly within DataMiner.

**Benefit**: Troubleshooting time is reduced, enabling faster restoration of services and minimizing the impact on viewers.

### Configuration Validation

**Challenge**: Misconfigured source, primary, or output stream settings can lead to caption loss or incorrect stream routing.

**Solution**: The connector exposes stream configuration information for each Alta-TS instance, allowing operators to validate channel setups directly from DataMiner.

**Benefit**: Configuration issues can be identified proactively, reducing service interruptions and operational errors.
