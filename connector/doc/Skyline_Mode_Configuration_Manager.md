---
uid: Connector_help_Skyline_Mode_Configuration_Manager
---

# Skyline Mode Configuration Manager

## About

The **Skyline Mode Configuration Manager** is a generic DataMiner driver that provides a centralized way to manage and expose operational mode configuration.  
It allows users to view the current mode and last mode change, while maintaining a configurable set of mode-specific properties that can be reused across alarming, trending, and automation workflows.

This connector serves as a lightweight, shared configuration element for other applications, scripts, and dashboards within the DataMiner ecosystem.

## Key Features

- **Centralized mode configuration**  
  Maintain all mode-related settings in a single, dedicated element.

- **Read-only mode visibility**  
  Exposes the current operational mode and the last mode change for consumption by other solutions.

- **Configurable mode properties**  
  Define custom labels, alarming properties, and trending properties per mode.

- **UI-driven table management**  
  Add, edit, and delete mode configurations directly from the DataMiner UI without scripting.

- **Generic and reusable design**  
  Designed to be easily integrated into multiple solutions, dashboards, and automation workflows.

## Use Cases

### Standardized alarming and trending behavior

**Challenge**:  
Different applications and scripts require consistent alarming and trending behavior based on the current operational mode.

**Solution**:  
Use the Mode Configuration table to define mode-specific alarming and trending properties in one central location.

**Benefit**:  
Ensures consistent behavior across solutions while reducing duplicated configuration logic.

### Mode-aware automation workflows

**Challenge**:  
Automation scripts need awareness of the current operational mode to make safe and context-aware decisions.

**Solution**:  
Consume the Current Mode and Mode Configuration data from the connector within Automation scripts.

**Benefit**:  
Simplifies script logic and improves maintainability by externalizing mode configuration.

### Operational visibility and dashboards

**Challenge**:  
Operators need clear visibility into the active mode and when it last changed.

**Solution**:  
Expose the connector parameters on dashboards or within custom applications.

**Benefit**:  
Improves operational awareness and traceability of mode changes.

## Technical Reference

### Prerequisites

- Appropriate user permissions to modify table entries if configuration changes are required

> [!NOTE]
> For detailed technical information, refer to our  
> [technical documentation](xref:Connector_help_Skyline_Mode_Configuration_Manager_Technical).
