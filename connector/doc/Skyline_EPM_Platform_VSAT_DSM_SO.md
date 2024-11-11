---
uid: Connector_help_Skyline_EPM_Platform_VSAT_DSM_SO
---

# Skyline EPM Platform VSAT DSM SO

This connector is used to gather information **via inter-element communication** that will be exported to a location used by the **Generic Sun Outage** connector. The information gathered consists of key parameters used during the calculation of sun outages. This connector is purely a system connector with this sole responsibility.

## About

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware            |
|-----------|-------------------------------|
| 1.0.0.x   | Not available (system connector) |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Configuration

### Connections

#### Virtual connection

This connector uses a virtual connection and does not require any input during element creation.

## How to use

As this is mainly a system connector, not much user interaction is needed. Below you can find more information on the different functionalities in the connector.

### General

Clicking the **Update** button will perform a **full update of the system**. It will:

- Get the latest subscribers from the EPM VSAT Subscriber Manager for both the **Earth Stations** and the **Satellites table**.
- Retrieve the data from these subscribers.
- Export information for both earth stations and satellites to the relevant **CSV file**.

### Configuration

#### Export Configuration

The following functionalities are available within this section:

- **File Export**: Allows you to control the connector exporting the information gathered from the subscribers to a CSV file.
- **File Export Path**: Determines the path used to export the CSV file.
- **Export Processing Time**: Allows you to control how **frequently** the system will gather new data to be exported.
- **Apply:** Allows you to do a **manual update** of the export logic.

#### Subscribers Configuration

The following functionalities are available within this section:

- **Update Subscribers**: Allows you to control the update of the subscribers table from the EPM VSAT Subscription Manager.
- **Subscribers Timer**: Allows you to control how **frequently** the system will get updates from the EPM VSAT Subscription Manager.
- **FE DMA ID**: DataMiner Agent ID of the front-end DMA where the files will be located and where the EPM VSAT Subscription Manager script needs to be executed.
- **Subscriptions Folder Path**: The path where the files for the subscriptions tables will be stored. Note that this folder path needs to be written like a local path, but it will not be a local path to the hosting Agent but to the front-end Agent.

### ES Subscribers

The following functionalities are available on this page:

- Adding an entry to the subscriber table:

  1. Right-click anywhere within the table.
  1. Select **Add New Row** in the context menu.
  1. Fill in the necessary information in the pop-up window.
  1. Click OK.

- Editing an entry in the subscriber table:

  1. Right-click the entry you want to edit.
  1. Select **Edit ES Subscriber** in the context menu.
  1. Edit the necessary information in the pop-up window.
  1. Click OK.

- Deleting entries from the subscriber table:

  1. Select the entries you want to delete.
  1. Right-click the entries.
  1. Select **Delete selected row(s)** in the context menu.

- Clearing all entries from the table:

  1. Right-click anywhere within the table.
  1. Select **Clear Table** in the context menu.

- Updating the table: Click the update button at the bottom of the table to update it with the latest information from EPM VSAT Subscriber Manager.

### Sat Subscribers

The following functionalities are available on this page:

- Adding an entry to the subscriber table:

  1. Right-click anywhere within the table.
  1. Select **Add New Row** in the context menu.
  1. Fill in the necessary information in the pop-up window.
  1. Click OK.

- Editing an entry in the subscriber table:

  1. Right-click the entry you want to edit.
  1. Select **Edit Sat Subscriber** in the context menu.
  1. Edit the necessary information in the pop-up window.
  1. Click OK.

- Deleting entries from the subscriber table:

  1. Select the entries you want to delete
  1. Right-click the entries.
  1. Select **Delete selected row(s)** in the context menu.

- Clearing all entries from table:

  1. Right-click anywhere within the table.
  1. Click **Clear Table**

- Updating the table: Click the update button at the bottom of the table to update it with the latest information from EPM VSAT Subscriber Manager.
