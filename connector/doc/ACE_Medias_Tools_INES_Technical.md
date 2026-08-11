---
uid: Connector_help_ACE_Medias_Tools_INES_Technical
---

# ACE Medias Tools INES

## About

The **ACE Medias Tools INES** connector monitors and controls telephone codec lines managed by the INES call-management platform via its REST API. It provides real-time call state visibility, audio status monitoring, and line configuration management, polling all lines every 10 seconds.

## Configuration

### Connections

#### HTTP Connection - Main

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The IP address or hostname of the INES server.
- **IP port**: The IP port of the INES REST API (default: *443*).
- **Bus address**: *bypassProxy*.

## How to Use

### General

The **General** page contains two tables that together give a complete picture of every codec line managed by INES.

#### Lines Info

The **Lines Info** table lists all lines retrieved from the INES system. Each row represents one codec line and shows its live operational state.

| Column | Description |
|--------|-------------|
| **Name** | Human-readable name assigned to the line |
| **Label** | Short display label for the line |
| **Description** | Extended description as configured on the device |
| **State** | *Ready*: no active call; *Connected*: a call is established |
| **Audio** | *Present*: audio signal detected; *Absent*: no signal |
| **Muted** | *Muted*: audio output suppressed; *Unmuted*: audio active |
| **Direction** | *Idle*, *Incoming*, or *Outgoing* |
| **Connected Address** | Remote IP address or hostname for the active call; empty when idle |
| **SIP Registrar** | SIP registrar server associated with the line's SIP account |

The **Start** and **Stop** buttons in each row initiate and terminate calls on the selected line. Both actions display a confirmation prompt before the request is sent to the device.

> [!NOTE]
> After a Start or Stop action, the connector immediately re-polls the active call endpoint and then refreshes the full line list. As a result, state changes are reflected quickly without having to wait for the next timer cycle.

#### Line Capability

The **Line Capability** table shows the audio codec protocol configuration for each line. This data is populated from the same `/api/rest/lines` poll that populates the **Lines Info** table.

| Column | Description |
|--------|-------------|
| **Protocol Name** | Audio codec protocol (e.g., AES67, G.711, MPEG) |
| **Address** | Primary IP or multicast address for the audio stream |
| **Data Rate** | Profile name (e.g., Mono, Stereo, 5.1) |
| **Data Rate Nb of Channels** | Number of audio channels in the data rate profile |
| **Transport** | Network transport protocol (e.g., RTP, UDP, TCP) |
| **Separation** | Channel separation mode (e.g., none, interleaved) |
| **Sampling Rate** | Audio sampling rate in Hz (e.g., 48000 for 48 kHz) |

To update a line's codec configuration, right-click a row and select **Edit Line Capability**. This opens a form pre-filled with the current values. Once submitted, the setup is sent to `POST /api/rest/lines/:lineId/setup`, and the full line list is refreshed automatically.
