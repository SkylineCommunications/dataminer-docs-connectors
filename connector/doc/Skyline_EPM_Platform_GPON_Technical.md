---
uid: Connector_help_Skyline_EPM_Platform_GPON_Technical
---

# Skyline EPM Platform GPON

## About

Skyline EPM Platform GPON is a virtual DataMiner connector for GPON Experience and Performance Management (EPM) topology and CPE data. A single connector package is deployed as a Backend element, a Frontend element, or both, depending on the configured element role.

The Backend imports and retains collector provisioning data. The Frontend coordinates provisioning requests and presents the CPE-facing hierarchy. The topology includes networks, markets, hubs, OLTs, slots, ports, ONTs, subscribers, and passive split route, distribution, and FAT entities.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require connection input when the element is created.

### Initialization

1. Create the element and set **Element Manager Type** on the **Configuration** page:

   | Role | Value | Purpose |
   |---|---:|---|
   | Backend | 0 | Imports collector provisioning data and maintains Backend topology tables. |
   | Frontend | 1 | Coordinates requests and presents the CPE-facing topology. |

1. Configure the **File Import Path** and **File Export Path** for the GPON EPM provisioning workflow.

   - Choose the corresponding directory type for each path.
   - When a path is remote, configure the **System Username** and **System Password** that allow the DataMiner process to access it.
   - Ensure the participating EPM elements use paths that are accessible for the required file exchange.

1. Register the elements that participate in the workflow using the `DMA_ID/Element_ID` format.

   - On a Backend element, register the GPON OLT collector elements.
   - On a Frontend element, register the GPON Backend elements, GPON OLT collector elements, and the Frontend element.

> [!WARNING]
> Do not use production CSV exports or credentials as documentation or test fixtures. Use only sanitized provisioning data.

## How to Use

### Provisioning

Use the **Provision** control to queue a provisioning cycle. The Backend processes its ID Buffer entries. The Frontend processes received requests in its Messaging Buffer and imports the configured CSV data to populate the GPON hierarchy.

The Frontend communicates through InterApp calls and processes the following workflows:

- `EPM` for the main GPON topology.
- `EPM GPON Passives` for passive split entities.

### Reset

Use the **Reset** control to start a reset provisioning cycle. Imported keys are accumulated while queued work is processed. After all applicable entries complete, stale topology rows that are not part of the new data set are removed.

> [!NOTE]
> Avoid clearing buffer rows during an active provisioning or reset cycle unless recovering from a known failure. Premature removal can prevent completion and stale-row cleanup.

### Operational pages

Use the Backend and Frontend configuration pages to inspect and configure the role-specific settings. The Messaging Buffer and ID Buffer views help diagnose queued work. The network, market, hub, OLT, slot, port, ONT, subscriber, and split pages expose the provisioned topology.

## Notes

- This connector does not directly poll GPON hardware. It depends on the GPON EPM collectors and their supplied provisioning data.
- The minimum supported DataMiner version is `10.3.0.0 - 12752`.
- The connector does not export child connectors.
