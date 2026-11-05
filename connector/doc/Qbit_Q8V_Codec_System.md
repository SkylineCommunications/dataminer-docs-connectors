---
uid: Connector_help_Qbit_Q8V_Codec_System
---

# Qbit Q8V Codec System

## About

The Qbit Q8V Codec System connector provides status information and configuration control for the Q866 SMB Internet Radio Transcoder. This device converts 4 to 6 Icecast/Shoutcast internet radio streams into a DVB-compliant MPEG-2 transport stream for OTT and cable network distribution. Signals are made available via IP (Ethernet).

## Key Features

- **Device status monitoring**: View system parameters, software versions, interfaces, and all operational components.

- **Input management**: Configure web streams and transport streams from the Inputs page.

- **Input selector configuration**: Manage input selector routing and associations.

- **Encoder control**: Monitor and configure encoders, linking them to input selectors or audio sources.

- **Transport stream management**: Manage MPEG-2 transport streams, including services and destinations.

## Use Cases

### Integrating Web Radio Streams in Existing Networks

**Challenge**: Integrating multiple web radio streams into an existing OTT or cable network requires a reliable method for transcoding and packaging streams.

**Solution**: The connector enables configuration of Icecast/Shoutcast streams and outputs them as DVB-compliant MPEG-2 transport streams.

**Benefit**: Simplifies end-to-end integration of web radio into professional broadcast environments.

### Real-Time Service Monitoring

**Challenge**: Operators need visibility into encoder behavior and input routing to ensure stable service delivery.

**Solution**: The Encoders and Input Selectors pages provide real-time monitoring and configuration tools.

**Benefit**: Faster troubleshooting and optimized signal flow management.

### Managing TS Services when Scaling Distribution

**Challenge**: Managing transport stream services can be complex when scaling distribution.

**Solution**: The MPEG-2 TS and Services pages provide structured management of output transport streams.

**Benefit**: Streamlined distribution configuration with clear destination and service control.

## Prerequisites

- **DataMiner 10.0.0 or higher** is required because of the SLManagedScripting C#7 syntax.

- An **HTTP connection** is needed for device communication, for which IP address/host and port (default 443) will need to be filled in.

- A **valid username and password** will have to be filled in on the General page of the element to authenticate.
