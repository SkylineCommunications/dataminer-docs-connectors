---
uid: Connector_help_Proximus_File_Manager
---

# Proximus File Manager

## About

The Proximus File Manager is a custom DataMiner connector designed to streamline the monitoring of command outputs. By receiving commands and their results from other DataMiner elements via InterApp Communication, it provides a centralized and intelligent way to track critical information. The connector automatically processes these outputs, categorizing them into easy-to-read tables for effective monitoring and trending.

## Key Features

- **Centralized Custom Command Outputs**: Gathers command outputs from various DataMiner elements into a single, centralized location, eliminating the need to check multiple sources.
- **Numeric and String Monitoring**: Automatically processes raw command outputs and categorizes them into dedicated Numeric and String tables, allowing for monitoring and trending.
- **Context Menus**: Synchronized removal across tables.
- **Customizable Output Description**: Allows users to set a custom description for any command output in the numeric and string tables.

## Use Cases

**Challenge**: Monitoring outputs from various custom commands is time-consuming and inefficient due to a lack of a centralized tool.

**Solution**: The Proximus File Manager automatically receives and processes these commands via InterApp Communication, consolidating all outputs into a single, easy-to-navigate interface.

**Benefit**: This centralizes all your critical command outputs, providing a unified view that saves time and improves operational efficiency.

## Technical Reference

### Prerequisites

- **InterApp Communication**: The connector receives messages via InterApp Communication, so other elements must be configured to send commands to this element.

> [!NOTE]
> For detailed technical information, refer to our [technical documentation page](xref:Connector_help_Proximus_File_Manager_Technical).
