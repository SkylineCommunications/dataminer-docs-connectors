---
uid: Connector_help_Qbit_Q8V_Codec_System
---

# Qbit Q8V Codec System

## About

The Qbit Q8V Codec System connector provides status information and configuration control for the Q866 SMB Internet Radio Transcoder. This device converts 4 to 6 Icecast/Shoutcast internet radio streams into a DVB-compliant MPEG-2 transport stream for OTT and cable network distribution. Signals are made available via IP (Ethernet).

## Key Features

- **Device Status Monitoring**: View system parameters, software versions, interfaces, and all operational components.

- **Input Management**: Configure Web Streams and Transport Streams from the Inputs page.

- **Input Selector Configuration**: Manage input selector routing and associations.

- **Encoder Control**: Monitor and configure encoders, linking them to input selectors or audio sources.

- **Transport Stream Management**: Manage MPEG-2 transport streams, including services and destinations.

## Use Cases

### Use Case 1

**Challenge**: Integrating multiple web radio streams into an existing OTT or cable network requires a reliable method for transcoding and packaging streams.

**Solution**: The connector enables configuration of Icecast/Shoutcast streams and outputs them as DVB-compliant MPEG-2 transport streams.

**Benefit**: Simplifies end-to-end integration of web radio into professional broadcast environments.

### Use Case 2

**Challenge**: Operators need visibility into encoder behavior and input routing to ensure stable service delivery.

**Solution**: The Encoders and Input Selectors pages provide real-time monitoring and configuration tools.

**Benefit**: Faster troubleshooting and optimized signal flow management.

### Use Case 3

**Challenge**: Managing transport stream services can be complex when scaling distribution.

**Solution**: The MPEG-2 TS and Services pages provide structured management of output transport streams.

**Benefit**: Streamlined distribution configuration with clear destination and service control.

## Technical Reference

### Prerequisites

- **HTTP Connection** is needed for device communication, requiring IP address/host and port (default 443).

- **Valid Username and Password** are needed to authenticate on the General page.

- **DataMiner Version 10.0.0.0 – 9118 or higher** is required due to SLManagedScripting C#7 syntax.




