---
uid: Connector_help_beIN_Feed_Request_Preset_Manager
---

# beIN Feed Request Preset Manager

The beIN Feed Request Preset Manager is a connector used to monitor preset workflows at BeIN.

## About

### Version Info

| Range              | Features                        | Based on | System Impact |
|--------------------|---------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Monitoring of preset workflows. | -        | -             |

### System Info

| Range   | DCF Integration | Cassandra Compliant | Linked Components | Exported Components |
|---------|-----------------|---------------------|-------------------|---------------------|
| 1.0.0.x | No              | Yes                 | BeIN LCA          | -                   |

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

On the **General** page, use the **Remove Unused Presets After** parameter to define for how many months a preset should remain valid after its last use.

## How to use

When you load a preset using the BeIN low-code app, a message is sent to the element running this connector. The message is processed, the load count is incremented, and the last used field is updated.

To remove presets that have not been used within the defined period from the table and the system, you can configure the **Remove Unused Presets After** parameter (see [Initialization](#initialization)) or click the **Remove** button to remove them manually.
