---
uid: Connector_help_ZTE_ZENIC_ONE_R22_ZXONE_9700E_Technical
description: "Technical details for the exported ZTE ZENIC ONE R22 ZXONE 9700E DVE connector, including export mapping, pages, and operational scope."
---

# ZTE ZENIC ONE R22 ZXONE 9700E Technical

## About

The ZTE ZENIC ONE R22 ZXONE 9700E connector is an exported protocol (DVE) generated from the ZTE ZENIC ONE R22 parent connector.

Each DVE represents a discovered node and exposes node-specific monitoring data through exported parameters and tables.

## Configuration

### DVE Export Definition

The DVE is generated from the parent connector export rules with the following mapping:

- Exported protocol name: **ZTE ZENIC ONE R22 ZXONE 9700E**.
- Source table for DVE creation: **availableNodes** (table 1000).
- Source key column: **availableNodesMeId** (PID 1001).
- DVE display label source: **availableNodesUserLabel** (PID 1002).
- Internal DVE reference column: **availableNodesDVE** (PID 1036).

### Runtime Prerequisites

- The parent connector element must be running and discovering nodes in the **availableNodes** table.
- DVE creation and lifecycle are driven by the parent connector export rules and runtime data.

## How to use

### General

Use this page to view node-level general information and status for the exported DVE.

### Alarms

Use this page to monitor node-related alarm data exported from the parent connector alarm domain.

### Directional Optical Ports

Use this page to monitor directional optical port information associated with the node.

### Ports OAC

Use this page to monitor OAC port information associated with the node.

### Optical Channel and Interface Metrics

Use this page to monitor optical channel and interface metrics associated with the node.

### Slot Status

Use this page to monitor slot-level hardware status.

### Fan Status

Use this page to monitor fan-level hardware status.

### Termination Points

Use this page to monitor node termination point status.

### Debug

The Debug page is hidden by default and controlled by an exported debug-page visibility setting.

## Technical Notes

- The exported DVE surface is primarily monitoring-oriented.
- Exported tables are linked to the parent node key through foreign-key mapping.
- Available write capability on the DVE is limited to local debug-page visibility behavior.