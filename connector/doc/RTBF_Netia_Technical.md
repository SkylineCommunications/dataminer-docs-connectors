---
uid: Connector_help_RTBF_Netia_Technical
---

# RTBF Netia

## About

The **RTBF Netia** connector provides an overview and full control over all **playout servers** and **player devices** hosted on Netia.

**Netia** is audio broadcasting software used by radio stations.

## Configuration

### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

- **IP address/host**: The IP address or host where Netia is hosted.
- **IP port**: The port number of the Netia service.

## How to Use

### General Page

This page contains a **Playout Servers** table displaying relevant information about each server. Next to this table, a **Status** parameter indicates the polling status. This status reflects the success of polling for playout servers, player devices, and jingle content for each device. If the status indicates an alarm state, this means one or more polling cycles failed.

### Devices Page

This page contains a **Player Devices** table and a **Jingles** table. The Player Devices table includes information about each device and provides command buttons (**Start**, **Acquire**, **Stop**) for each device.

If a player device is of type **Hotkey Player**, you can choose a specific **Run ID** to start or stop, using the **Selected Run** dropdown column. This column is populated from the **Jingles** table, which provides details about the content loaded on each hotkey player.

#### Load Jingle Subpage

The **Devices page** also includes a button that opens the **Load Jingle** subpage. From this subpage, you can easily load any jingle pack. It contains three parameters:

- **Device ID**: A dropdown parameter listing all available hotkey player IDs. This list is refreshed after each device polling cycle (every 10 minutes).
- **Jingle Pack ID**: A field where you can enter the ID of the jingle pack to be loaded onto the selected device.
- **Load Jingle**: A button used to initiate the loading of the selected jingle pack. The operation will succeed if the jingle pack ID is valid and exists in the database.
