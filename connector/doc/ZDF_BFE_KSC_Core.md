---
uid: Connector_help_ZDF_BFE_KSC_Core
---

# ZDF BFE KSC Core

This custom connector retrieves information from a BFE KSC 2 RU/19" control panel with 72 buttons using the SC05 BD-Protocol.

## About

### Version Info

| Range              | Key Features                                                         | Based on | System Impact |
|--------------------|----------------------------------------------------------------------|----------|---------------|
| 1.0.0.x [SLC Main] | Retrieves groups and labels from the source and destination layouts. | -        | -             |

### Product Info

| Range   | Supported Firmware |
|---------|--------------------|
| 1.0.0.x | v1.0               |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Smart-Serial Connection - Main

This connector uses a smart-serial connection and requires the following input during element creation:

SMART-SERIAL CONNECTION:

- **IP address/host**: should always be set to *any*.
- **IP port**: The IP port of the destination (default: *2011*).

## Requirements

In order for the connector to properly retrieve the required information from the control panel, a couple of requirements regarding its layout are needed.

![Control Panel Layout](~/connector/images/ZDF_BFE_KSC_Core_ControlManager.png)

### 1. Sections

The two buttons in the purple box are considered to be **sections**. The top one is considered to display the input groups and the bottom one is considered to display the output groups. The colors and text of these buttons can be freely adjusted, but their positions cannot.

### 2. Groups

Every button in the green box that has a text and a color is considered a **group**. The active group (= the currently selected group) is determined by the green background color (RGB 0;255;0). This means that any group can be added, with any text or background color except for green (RGB 0;255;0), as long as it is part of the green box. The color to visualize the active group cannot be adjusted.

### 3. Labels

Every button in the red box that has a text and a color is considered a **label**. Labels can be added freely with any text or background color as long as they reside in the red box.