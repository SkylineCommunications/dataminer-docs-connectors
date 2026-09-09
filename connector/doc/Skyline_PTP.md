---
uid: Connector_help_Skyline_PTP
description: Discover how to use the Skyline PTP connector to monitor PTP network topologies, grandmasters, and clock synchronization in DataMiner.
---

# Skyline PTP

The **Skyline PTP** connector is used as an application in the **DataMiner PTP Solution** to monitor the different PTP devices in a network.

For range 2.0.0.x, monitoring and configuration are handled via the **PTP Monitor** custom web application. For range 1.0.0.x, a Visio file provides access to the functionality of the PTP Solution.

## About

### Version Info

| Range                | Key Features                                                                                                                                                                     | Based on   | System Impact   |
|----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|-----------------|
| 1.0.0.x              | Overview of PTP devices. Monitoring of active grandmaster.                                                                                                                       | -          | -               |
| 2.0.0.x [SLC Main]   | In-connector mediation replacing Standard DataMiner PTP Device. Integration with PTP Monitor custom web application. Removal of Visio file and legacy setup automation scripts. | -          | -               |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | N/A                    |
| 2.0.0.x   | N/A                    |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components                                                                                                                                            | Exported Components     |
|-----------|---------------------|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | Standard DataMiner PTP Device (mediation protocol) PTP_SetupWizard (configuration automation script) PTP_SetupWizard_Roles (configuration automation script) | -                       |
| 2.0.0.x   | No                  | Yes                     | PTP Monitor Web Application (DataMiner PTP Solution 2.0.0)                                                                                                   | -                       |

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

This element should not be created manually:

- For range 2.0.0.x, creation is handled through the **PTP Monitor** custom web application.
- For range 1.0.0.x, creation is handled using the **PTP_SetupWizard** automation script.

For more information, refer to the [Initialization](#initialization) section below.

### Initialization

The initialization process depends on the connector range:

- **Range 2.0.0.x**: Configuration and domain setup are handled directly through the **PTP Monitor** custom web application (via the **Admin** page, using the **Add Domain** and **Role Assignment** wizards). The legacy `PTP_SetupWizard` and `PTP_SetupWizard_Roles` automation scripts and Visio visual pages are removed in range 2.0.0.x.
- **Range 1.0.0.x**: The configuration of the Skyline PTP application and the full DataMiner PTP Solution must be done using the PTP_SetupWizard and PTP_SetupWizard_Roles automation scripts.

For range 1.0.0.x, the **PTP_SetupWizard** script must be executed initially to configure the DataMiner PTP Solution. This script will:

- Create the Top view for the PTP Solution items.
- Create the Skyline PTP element.
- Execute the initial configuration of the Skyline PTP element.
- Execute the PTP_SetupWizard_Roles automation script.

The **PTP_SetupWizard_Roles** script is used to configure the PTP devices and update this in the Skyline PTP element. This script is executed from the PTP_SetupWizard script once the initial configuration is done. However, it can also be manually executed later to update the PTP devices managed by the Skyline PTP application. The PTP_SetupWizard_Roles script will:

- Configure the PTP devices in the Skyline PTP application with their respective roles.
- Update the PTP Role element property on each PTP device added to the PTP Solution.
- Create a PTP information template for each protocol that has at least 1 element added as PTP device in the Solution.

When both of these scripts have been executed, the PTP Solution should be fully configured and the Skyline PTP element will start monitoring the PTP topology.

### Redundancy

There is no redundancy defined.

## How to use

For range 2.0.0.x, monitoring is done through the **PTP Monitor** web application. Refer to the [Skyline PTP Technical](xref:Connector_help_Skyline_PTP_Technical) page for technical parameters and the supported connectors list.

For range 1.0.0.x, the data pages of the Skyline PTP element are not intended to be used directly. All the necessary data can be found on the Visual pages. For more information on how to use these pages, refer to the DataMiner PTP section in the DataMiner Help.
