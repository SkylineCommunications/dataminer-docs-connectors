---
uid: Connector_help_Imagine_Communications_SX_Pro_Multiviewer_Technical
---

# Imagine Communications SX Pro Multiviewer

## About

This connector uses the **SNMP** protocol to gather status information from the **SX Pro Multiviewer** card, which is usually installed inside a Platinum or IP3 router or matrix. The connector also receives SNMP **traps** from the multiviewer card.

## Configuration

### Connections

#### SNMP Connection — Main

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

| Setting | Value |
|---------|-------|
| **IP address/host** | The polling IP of the device |
| **IP port** | The port of the connected device (default: *161*) |
| **Get community string** | The community string used when reading values from the device (default: *public*) |
| **Set community string** | The community string used when setting values on the device (default: *private*) |

## How to Use

Enabling and using traps can capture short duration alarms that occur outside of the normal connector polling cycles.

On the **Traps** page's **Auto Clear** subpage, the auto-clear method can be configured, either by configuring **Max. Number** of traps, **Max. Duration** of traps or **Both (Max. Number and Max. Duration)**, or by clearing **Upon Alarm Polling**. The table size will remain constant, but when the max. number has been reached, the oldest table entries will be purged to make room for new entries. You can also clear all current traps by clicking the **Clear All Traps Now** button on this subpage.

## Notes

In order to receive SNMP traps with this element, it is necessary to make the following configuration changes to the device using its web interface GUI:

- **Hardware Configuration\SNMP**: Set **Trap Destination** to the **DMA IP** or the **Virtual IP** when using a 1:1 Failover DMA configuration.
- **Time Code: Trap Timestamps** are affected by this setting and care should be taken to select a proper time sync reference.
- **PC**: Allows you to set the **DMA IP** as the time source or the **Virtual IP** when using a 1:1 Failover DMA configuration.
  - **NTP**: Allows you to set **any NTP Server** in the network as the time source.
