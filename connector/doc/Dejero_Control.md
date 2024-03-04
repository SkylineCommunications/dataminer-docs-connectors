---
uid: Connector_help_Dejero_Control
---

# Dejero Control

Dejero Control is a cloud-based management system that provides the power and flexibility to centrally manage Dejero equipment via a web browser.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | Control API 2.0        |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The polling IP or URL of the destination.
- **IP port**: The IP port of the destination.

### Initialization

To initialize communication, you need to provide a Secret Key and Access ID on the **Connection Settings** page.

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to use

### General

This page displays the **Sources** and **Sources Details** tables.

Within the **Sources** table, the following actions are possible:

- **Start/Stop Video Stream**: Start or stop the live stream.
- **Live Assigment**: Assign, change, or unassign the source's live assignment.
- **Clip Assigment**: Assign, change, or unassign the source's clip assignment.
- **File Assigment**: Assign, change, or unassign the source's file assignment.

The **Sources Details** table contains the location and battery information of the source. The **Location Last Updated** and **Battery Last Updated** parameters indicate the last time the information was updated for that source.

### Connection Settings

This page displays the **Secret Key** and **Access ID** boxes, where the credentials for the HTTP API polling should be filled in.

### Receivers

This page displays the **Receivers** table, which contains the following columns: **Index**, **Serial Number**, **Name**, and **Type**.

### Outputs

This page displays the **Outputs** table, which contains the following columns: **Index**, **Serial Number**, **Name**, **Status**, and **Type**.

### Stations

This page displays the **Stations** table, which contains the following columns: **Index**, **Name**, and **Callsign**.

### Gateways

This page displays the **Gateways** table, which contains the following columns: **Index**, **Serial Number**, **Name**, and **Status**.

### Pools

This page displays the **Pools** table, which contains the following columns: **Index** and **Name**.

### Live Assignments

This page displays the **Live Assignments** table, which contains the following columns: **Index**, **Resource**, **Resource Name**, **Source Name**, and **Unassign**.

In the **Unassign** column, you can unassign the live assignment from the output.

### Clip Assignments

This page displays the **Clip Assignments** table, which contains the following columns: **Index**, **Receiver Name**, **Source Name**, and **Unassign**.

In the **Unassign** column, you can unassign the clip assignment from the receiver.

### File Assignments

This page displays the **File Assignments** table, which contains the following columns: **Index**, **Receiver Name**, **Source Name**, and **Unassign**.

In the **Unassign** column, you can unassign the file assignment from the receiver.
