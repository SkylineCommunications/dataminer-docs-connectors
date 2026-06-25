---
uid: Connector_help_MiT_Xperts_iSIMS
---

# MiT Xperts iSIMS

## About

The **MIT xperts iSIMS** is a DVB Service Information Management System used to generate, multiplex, and distribute PSI/SI tables (PAT, PMT, SDT, EIT, NIT, RST) across digital television and broadcast networks. This DataMiner connector communicates with the iSIMS server via **SNMP**, providing centralized monitoring of server health, configuration elements, input services, output transponders, data flows, and IP inputs — giving broadcast and playout engineers full operational visibility from a single pane of glass.

## Key Features

- **Server and element health monitoring**: Track the overall iSIMS server state, the combined state of all configuration elements, the running software version, and the count of erroneous elements, so operators can instantly assess platform health.

- **Configuration element oversight**: Monitor every configuration element in a dedicated table — including internal element ID, name, per-element state (Ok/Warn/Error), and XML configuration — with the ability to push updated element configuration back to the system.

- **Input service surveillance**: Watch DVB input services with full ONID/TSID/SID identification, owning element details, EIT schedule depth, update-timeout detection, and a detailed service state (Ok, Missing, TS No Signal, XML Warning, XML Error, Update Timeout).

- **Output transponder assurance**: Keep transponder outputs healthy by tracking ONID/TSID, owning element, and transponder state (Ok, Missing, Bitrate Too Low, Problem, Error), with custom user descriptions for easier identification.

- **Data flow visualization**: Surface the data flows between configuration elements — including source and destination element IDs and names plus flow configuration — to understand how content moves through the iSIMS processing chain.

- **IP input and SI repetition-rate analysis**: Inspect IP/multicast inputs in detail — IP address, port, source IP, network interface, FEC, PID pairs, and PAT/SDT/EIT/RST/NIT PIDs — together with measured repetition rates (in ms) for PAT/PMT, SDT (actual/other), and NIT (actual/other) tables.

- **Trap-driven alarming**: Receive and process SNMP traps from the iSIMS server, enabling event-driven awareness alongside scheduled polling.

- **Customizable polling**: Adjust polling periods per data group directly from DataMiner using the built-in Polling Manager, balancing responsiveness against network and device load.

## Use Cases

### Centralized DVB SI Platform Monitoring

**Challenge**: An iSIMS server orchestrates the generation of critical PSI/SI tables for an entire DVB network, yet a misconfiguration or failing element can silently degrade the broadcast signaling that set-top boxes rely on for service discovery and EPG.

**Solution**: The connector polls the server state, combined element state, and erroneous-element count every minute, while continuously tracking each configuration element's individual state — immediately surfacing warnings and errors within the DataMiner alarm console.

**Benefit**: Operations teams gain real-time, 24/7 insight into SI generation health from a central NOC, allowing them to catch configuration faults before they impact viewers' EPG and service navigation.

### Input Service and EPG Continuity Assurance

**Challenge**: Maintaining a reliable Electronic Program Guide and service signaling requires that every input service keeps delivering up-to-date EIT data; missing services, lost transport-stream signal, or stalled EIT updates can quietly break the on-screen guide.

**Solution**: The connector monitors the Input Service table in detail — exposing service state, EIT update timeouts, scheduled-event depth in days, and full DVB identification — so degraded or silent services are flagged the moment they deviate from normal.

**Benefit**: Broadcast engineers can proactively detect and resolve input-side issues, ensuring continuous, accurate EPG and service information for end viewers and reducing guide-related support tickets.

### Output Transponder and Data Flow Integrity Oversight

**Challenge**: As content is multiplexed and routed toward output transponders, operators need to verify that every transponder is healthy and that data flows between configuration elements remain intact across a complex processing chain.

**Solution**: The connector tracks output transponder state and bitrate-related conditions alongside a Data Flow table that maps source-to-destination element relationships, giving a clear topology of how content traverses the iSIMS system.

**Benefit**: Engineering teams achieve end-to-end traceability from input to output, simplifying fault isolation, validating routing changes, and minimizing the risk of dead or degraded transponders reaching the distribution network.

## Technical Reference

### Prerequisites

- **SNMP network access** is required between the DataMiner Agent and the MIT xperts iSIMS server (default SNMP port: 161).

- **DataMiner version 10.4.0.0 - 14003 or higher** is required as the minimum platform version for this connector.

### Polling Configuration

The connector uses the built-in Polling Manager to balance responsiveness with network efficiency. Default polling intervals are:

| Group | Interval | Data |
|--|--|--|
| System Up Time | 10 seconds | System uptime |
| Information | 1 minute | iSIMS server state, combined elements state, version, erroneous elements |
| Element Table | 1 minute | Configuration elements (ID, name, state, configuration) |
| Service Table | 1 minute | Input services (DVB IDs, owning element, schedule, update timeout, state) |
| Output Transponder Table | 1 minute | Output transponders (DVB IDs, owning element, state) |
| Data Flow Table | 1 minute | Data flows between configuration elements |
| General Parameters | 1 hour | System description, object ID, contact, name, location |
| Version | 1 hour | iSIMS software version |

> [!NOTE]
> Polling periods can be customized per group from the **Polling Settings** page using the Polling Manager.
