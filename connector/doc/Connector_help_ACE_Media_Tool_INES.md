---
uid: Connector_marketing_ACE_Media_Tool_INES
---

# ACE Media Tool INES

## About

The ACE Media Tool INES connector integrates AETA audio codecs into DataMiner via the INES REST API. It gives operators centralized visibility and control over all codec lines — including real-time call status, audio signal presence, and codec configuration — directly from the DataMiner platform.

## Key Features

- **Real-time line monitoring**: Continuously polls all codec lines every 10 seconds and displays their connection state (Ready/Connected), audio presence, mute status, and call direction in a unified Lines Info table.

- **Active call tracking**: Automatically retrieves details of the active call for each line, including the connected remote address, giving operators an instant view of ongoing communications.

- **One-click call control**: Start or stop calls on any codec line directly from the DataMiner UI using dedicated per-row action buttons, with a confirmation prompt to prevent accidental operations.

- **Line capability configuration**: Inspect and reconfigure codec line settings — including protocol (AES67, G.711, MPEG, etc.), IP address, data rate, transport, channel separation, and sampling rate — via an integrated context-menu-driven setup form.

- **SIP registrar visibility**: Exposes the SIP registrar server associated with each line's SIP account, enabling quick identification of registration issues without accessing the device directly.

## Use Cases

### Centralized Audio Codec Management for Live Broadcasting

**Challenge**: Broadcast engineers managing multiple AETA audio codec lines across a facility must log in to each device individually to check call status and reconfigure lines, leading to slow response times and operational blind spots during live events.

**Solution**: The ACE Media Tool INES connector brings all codec lines into a single DataMiner element, showing real-time state, audio presence, and call direction for every line. Engineers can start or stop calls and reconfigure line settings without leaving DataMiner.

**Benefit**: Reduced mean time to detect and resolve audio path issues during live productions, with all codec data available in one place alongside the rest of the broadcast infrastructure.

### Proactive Alarm Management for Audio Codec Lines

**Challenge**: Detecting lost audio signals or unexpected call disconnections on codec lines requires constant manual checking, making it difficult to respond before on-air impact occurs.

**Solution**: The connector exposes line state, audio presence, mute status, and call direction as monitorable parameters, allowing DataMiner alarm templates to be configured to automatically alert operators when a line drops audio or disconnects unexpectedly.

**Benefit**: Operators receive proactive alerts the moment a codec line changes state, enabling faster corrective action and reducing the risk of undetected audio outages affecting broadcasts.

### Streamlined Codec Reconfiguration During Production Changes

**Challenge**: Adapting codec line configurations (protocol, IP address, data rate, sampling rate) for different production setups is time-consuming and error-prone when done device by device through separate management interfaces.

**Solution**: The Line Capability table in DataMiner lists the full audio configuration of every line and provides a right-click context menu to open a pre-filled setup form for editing. Changes are pushed directly to the device via the INES API.

**Benefit**: Faster, less error-prone line reconfiguration during production turnarounds, with changes applied and confirmed within DataMiner without requiring direct device access.

## Technical Reference

### Prerequisites

- **AETA INES-compatible audio codec** with the INES REST API enabled and reachable from the DataMiner Agent.

- **Network connectivity** on port 443 (HTTPS) between the DataMiner Agent and the codec device. The connector defaults to HTTPS on port 443.

- **DataMiner 10.4.0.0-14003 or higher** is required to run this connector.

### HTTP API Interface

The connector communicates exclusively over HTTP(S) using the INES REST API. The following endpoints are used:

| Endpoint | Method | Purpose |
|---|---|---|
| `/api/rest/lines` | GET | Retrieve all codec lines and their current status |
| `/api/rest/lines/:lineId/active-call` | GET | Retrieve active call details for a specific line |
| `/api/rest/lines/:lineId/startcall` | POST | Initiate an outgoing call on a line |
| `/api/rest/lines/:lineId/endcall` | POST | Terminate the active call on a line |
| `/api/rest/lines/:lineId/setup` | POST | Apply a new audio configuration to a line |

### Polling Behavior

Lines are polled every 10 seconds via the fast timer. After a start-call or end-call action, the active call status is refreshed immediately to reflect the new line state.
