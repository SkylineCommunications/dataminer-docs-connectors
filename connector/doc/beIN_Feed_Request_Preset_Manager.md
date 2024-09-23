---
uid: Connector_help_beIN_Feed_Request_Preset_Manager
---

# beIN Feed Request Preset Manager

The **beIN Feed Request Preset Manager** is a connector used to monitor preset workflows at BeIN.

## About

### Version Info

|Range              |Features                             |Based on  |System Impact  |
|-------------------|-------------------------------------|----------|---------------|
|1.0.0.x [SLC Main] |Ability to monitor preset workflows  |-         |-              |

### System Info

|Range    |DCF Integration  |Cassandra Compliant  |Linked Components  |Exported Components   |
|---------|-----------------|---------------------|-------------------|----------------------|
|1.0.0.x  |No               |Yes                  |BeIN LCA           |                      |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

The user should define the number of months a preset remains valid after its last use in the `Remove Unused Presets After` parameter, located on the `General` page.

### Redundancy

There is no redundancy defined.

## How to use

When the user loads a preset using the BeIN Low Code App (LCA), a message is sent to the element running this connector. The message is processed, the load count is incremented, and the last used field is updated.

The user can then configure the `Remove Unused Presets After` parameter (see **Initialization** section) and, manually, by clicking the `Remove` button, presets that have not been used within the defined period are removed from the table and the system.
