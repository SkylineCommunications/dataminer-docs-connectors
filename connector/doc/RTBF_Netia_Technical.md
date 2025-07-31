---
uid: Connector_help_RTBF_Netia_Technical
---

# RTBF Netia

## About

RTBF Netia connector provides overview and full control over all Playout Servers and player devices that are hosted on Netia.

Netia is audio broadcasting software for audio stations.

## Configuration

### HTTP Connection

This connector uses an HTTP connection and requires the following input during element creation:

HTTP CONNECTION:

- **IP address/host**: The IP address/host where Netia is hosted.
- **IP port**: The IP port of Netia.

### Initialization

If element is created with valid hostname and port, connector will already start with polling cycle to show all available **Playout Servers** and **Player Devices** that are hosted on those playout servers.

## How to Use

Connector contains two pages:
- **General Page**: Contains Playout Servers table that is showing playout servers with all relevant informations. Next to playout servers table, status parameter is shown that is indicating status of all polled informations. That parameter is reused when we poll both playout servers, player devices as well as all jingle content for each device. If status is in alarm state, it means that some of mentioned polling cycles didn't succeded.
- **Devices Page**: Contains Player devices table and Jingles table. Devices table contains all informations about each device as well as command buttons for Start, Acquire and Stop for each Player device. If Player is Hotkey Player type, we can also chose which Run ID we want to start or stop for that specific Hotkey Player with **Selected Run** dropdown column. That column is filled in by **Jingles table**. Jingles table provides all informations about content that is loaded on every Hotkey Player Device.

Devices Page has **Load Jingle** subpage. From Load Jingle subpage we can easly load any jingle pack we want. On Load Jingle page we have three parameters:
- **Device ID**: Dropdown parameter where we have IDs of all avilable Hotkey Players. That dropdown is refreshed always after every device polling cycle (10 minutes).
- **Jingle Pack ID**: Parameter were we provide ID of jingle pack that we want to load on specific device.
- **Load Jingle**: Button on which we are trying to load jingle pack on device. Load will succeed if jingle pack is valid ID and if we have that jingle pack ID in database. 