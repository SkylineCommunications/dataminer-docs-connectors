---
uid: Connector_help_Nokia_Altiplano_OLT_Technical
---

# Nokia Altiplano OLT

## About

The **Nokia Altiplano OLT** connector is an integral component of the Nokia Altiplano solution. It is a virtual connector designed to present operational data from Nokia OLT (Optical Line Terminal) devices.

## Configuration

### Connections

#### Virtual Connection

This connector uses a virtual connection and does not require any input during element creation.

### Initialization

Upon creation of the element, the user may proceed to configure the import file settings. If the **Import Directory File** parameter is set to *Remote*, it is mandatory to specify the corresponding credentials under the **System Credentials** section, including the *System Username* and *System Password* fields.

## How to use

### Configuration

On this page, you can define essential parameters for the connector. The following section are available for setup:

- **System Credentials**: Provide credentials required for system-level access: **System Username** and **System Password**.

Additionally, you can specify an import folder to get the files generated from API responses or Nokia Altiplano Kafka element. This folder can be configured as either:

- **Local Folder**: Accessible directly from the host system.
- **Remote Folder**: Requires valid system credentials for authentication and access.

### Uplink

This page presents comprehensive information pertaining to the uplink ports of the OLT device. The displayed data is sourced from both Kafka streams and Altiplano API endpoints, ensuring a complete and synchronized view of uplink-related metrics and status.

### InterApp Messages

This page provides visibility into the InterApp communication activity of the element:

- **Last InterApp Message**: Indicates the timestamp of the most recent update to either the Inbound or Outbound table.
- **Max InterApp Messages Recorded**: Defines the maximum number of records to retain in each table. Once the limit is reached, older entries are automatically removed.
- **Inbound Table**: Displays messages received by the element via InterApp.
