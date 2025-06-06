---
uid: Connector_help_Starlink_Enterprise_-_User_Terminal
---

# Starlink Enterprise - User Terminal

The Starlink Enterprise - User Terminal connector is exported by the parent connector [Starlink Enterprise](xref:Connector_help_Starlink_Enterprise). For each known user terminal, a separate child element (or "DVE", i.e. dynamic virtual element) using this connector will automatically be created. These DVEs contain only data related to the user terminal.

## About

### Product Info

| Range     | Supported Firmware |
|-----------|--------------------|
| 1.0.0.x   | v1                 |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Initialization

The element using this connector can only be created by the parent element using the [Starlink Enterprise](xref:Connector_help_Starlink_Enterprise) connector. No additional configuration is necessary.

## How to Use

This connector is automatically generated by the Starlink Enterprise connector, range 1.0.0.x. For each entry in the **User Terminal DVEs** table, a separate dynamic virtual element (DVE) can be created. The name of such a DVE will be the ID of the corresponding user terminal.

To create an element, enable the **DVE Creation** toggle button for that specific terminal in the **User Terminals** table of the parent element.

This connector cannot be used to create a standalone element. You need to create a parent element using the Starlink Enterprise connector to be able to see the exported child elements.

### General Page

All telemetry data can be found on the General page.

### Alerts Page

Each row in the **Alerts** table represents an alert from a user terminal (not from a router). Alerts will persist for as long as they are active.

The **User Terminal Device ID** column in this table is hidden by default. You can show it by right-clicking the table column header, selecting **Columns**, and then selecting this column.

