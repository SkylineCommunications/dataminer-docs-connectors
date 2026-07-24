---
uid: Panasonic_KAIROS
---

# Panasonic KAIROS

## About

The Panasonic KAIROS connector provides comprehensive monitoring of Panasonic KAIROS live production systems in DataMiner.

KAIROS is Panasonic's next-generation IP-based live video production platform, used in broadcast facilities, live events, esports productions, houses of worship, corporate studios, and remote production environments. By integrating KAIROS into DataMiner, operators gain centralized visibility into the health, synchronization status, media resources, and signal flows of critical production infrastructure.

The connector enables engineering teams to proactively monitor system performance, detect synchronization problems before they impact production, and maintain operational awareness across complex live production environments.

## Key Features

### Synchronization Monitoring

Monitor the complete synchronization state of the KAIROS platform, including:

- PTP (Precision Time Protocol) synchronization status
- PTP Grandmaster information
- Genlock status
- Genlock source selection
- Genlock reference configuration

This allows operators to quickly identify timing issues that could affect production quality.

### System Health Monitoring

Gain visibility into overall system performance through:

- Device uptime
- GPU utilization
- Hardware sensor values
- Temperature monitoring
- Hardware status information

This helps engineering teams detect overheating, excessive resource consumption, and other operational risks before they become service-affecting issues.

### Media Resource Visibility

Monitor critical media resources within the KAIROS platform, including:

- RAM recording resources
- Media storage utilization
- Still-image storage usage
- Processing resource consumption

Historical trending enables capacity analysis and proactive resource planning.

### Network Performance Monitoring

Track network-related metrics that are essential in IP production environments:

- Network interface statistics
- Throughput monitoring
- High-bandwidth media traffic visibility

This enables rapid identification of network bottlenecks and throughput anomalies.

### Signal Flow Monitoring

The connector provides visibility into configured media flows across multiple transport technologies:

#### IP Flows

Monitor:

- IP Inputs
- IP Outputs
- Flow status
- Formats
- Tally information

#### SDI Flows

Monitor:

- SDI Inputs
- SDI Outputs
- Signal status
- Routing information
- Tally information

#### NDI Flows

Monitor:

- NDI Inputs
- NDI Outputs
- Flow status
- Format configuration
- Source information

#### HDMI Flows

Monitor:

- HDMI Inputs
- HDMI Outputs
- Format configuration
- Signal availability
- Source information

#### Streaming Flows

Monitor stream-based workflows including:

- RTP
- SRT
- RTMP

and other supported streaming formats configured within the KAIROS system.

### Asset and Hardware Tracking

Track installed hardware modules through serial number monitoring for:

- NIC cards
- SDI cards
- HDMI cards

This simplifies inventory management and hardware lifecycle tracking.

## Operational Benefits

### Reduce Production Risks

Synchronization issues often represent some of the most disruptive problems in live production environments. By continuously monitoring PTP and Genlock status, the connector helps operators identify potential issues before they impact on-air operations.

### Improve Operational Awareness

The connector consolidates system health, resource usage, synchronization status, and flow monitoring into a single DataMiner element, reducing the need to switch between multiple management tools.

### Accelerate Troubleshooting

When production issues occur, engineers can quickly verify:

- Timing and synchronization status
- Flow availability
- Signal presence
- Resource utilization
- Network performance

from a centralized monitoring platform.

### Enable Proactive Monitoring

Historical trending and alarming allow operations teams to identify developing issues long before they become critical events.

## Supported Monitoring Areas

| Area               | Description                                          |
| ------------------ | ---------------------------------------------------- |
| System Information | Model, version, manufacturer, system details, uptime |
| System Health      | GPU load and hardware sensor monitoring              |
| PTP                | Grandmaster and synchronization status               |
| Genlock            | Genlock state, source selection, lock status         |
| Media Resources    | Resource utilization and capacity information        |
| Network Statistics | Network performance and throughput metrics           |
| IP Flows           | Input and output flow monitoring                     |
| SDI Flows          | Input and output flow monitoring                     |
| NDI Flows          | Input and output flow monitoring                     |
| HDMI Flows         | Input and output flow monitoring                     |
| Stream Flows       | RTP, SRT, RTMP and other stream monitoring           |
| Hardware Inventory | Installed module serial numbers                      |

## Typical Use Cases

### Broadcast Facilities

Monitor production switchers and video processing infrastructure from a single operational dashboard.

### Remote Production

Ensure synchronization and media flow integrity across distributed production environments.

### Live Events

Maintain visibility into KAIROS systems used during concerts, conferences, sports productions, and other live events.

### Media Operations Centers

Integrate KAIROS monitoring into larger DataMiner operational workflows alongside routers, multiviewers, gateways, encoders, and other broadcast equipment.

## Requirements

- Panasonic KAIROS system
- SNMP enabled on the target device
- Network connectivity between DataMiner and the KAIROS platform
