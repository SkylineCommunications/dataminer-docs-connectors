---
uid: Connector_help_Imagine_Communications_SX_Pro_Multiviewer
---

# Imagine Communications SX Pro Multiviewer

## About

The **Imagine Communications SX Pro Multiviewer** is designed for baseband applications. Integration with the router platform provides a single system solution to enable an efficient use of space in complex broadcast and A/V monitoring environments.

The SX Pro hardware is installed in the output section of a Platinum or IP3 router frame. It takes inputs from the router where it is installed and combines those inputs on three or six different output displays. The size of the various options determines the number of outputs (three or six) and the number of inputs (8 to 64, with optional redundancy when installed in a 5RU, 9RU or 15RU frame).

### Key Features

- **PIP and display monitoring**: Track alarm, audio, tally, and Dolby E status for every video channel (PIP) shown across the multiviewer's displays.
- **Alarm summary**: Get a consolidated view of recent and current alarms, including UMD and tally PIP changes.
- **Trap capture**: Receive SNMP traps to catch short-duration alarms that fall between normal polling cycles.
- **Preset control**: Set the active preset per group directly from the element.

## Use Case

### Penalty Box Alarming for Failing Sources

**Challenge**: Operators need to be alerted quickly when a source falls into error, without having to scan every PIP across the multiviewer's regular displays.

**Solution**: When a PIP goes into alarm, a DataMiner correlation rule uses this connector's **PIP Alarm** status to trigger a rerouting of the affected source on a connected **Imagine Communications IP3 Router** to one of the PIPs on the multiviewer's dedicated penalty box display.

**Benefit**: Faster operator awareness of sources in error, since failing sources are automatically surfaced on the penalty box display instead of requiring manual monitoring.

## Prerequisites

- **SNMP access** to the SX Pro Multiviewer card.
- To receive **traps**, the device's **Trap Destination** must be configured to point to the DMA (see [Technical Reference](xref:Connector_help_Imagine_Communications_SX_Pro_Multiviewer_Technical#notes)).

## Technical Reference

> [!NOTE]
> For detailed technical information, refer to our [technical documentation](xref:Connector_help_Imagine_Communications_SX_Pro_Multiviewer_Technical).
