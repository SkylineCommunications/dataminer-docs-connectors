---
uid: Connector_help_beIN_Arvato_VPMS
---

# beIN Arvato VPMS Doha

The Arvato System's VPMS (Video Production Management System) is a solution designed to create, manage and process digital video content. With this solution, every integrated workflow, from ingest and production, transcoding and quality management to distribution, playout and archiving, can be managed. The beIN VPMS connector enables the monitoring of this solution.

## About

An **SNMP** connection is used in order to retrieve the necessary information. In addition, this connector can process SNMP traps in order to update the monitored parameters.

### Version Info

| Range                | Key Features     | Based on     | System Impact     |
|----------------------|------------------|--------------|-------------------|
| 1.0.0.x [SLC Main]   | Initial version  | -            | -                 |

### Product Info

| Range     | Supported Firmware     |
|-----------|------------------------|
| 1.0.0.x   | -                      |

### System Info

| Range     | DCF Integration     | Cassandra Compliant     | Linked Components     | Exported Components     |
|-----------|---------------------|-------------------------|-----------------------|-------------------------|
| 1.0.0.x   | No                  | Yes                     | -                     | -                       |

## Installation and configuration

### Creation

#### SNMP main connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: The polling IP of the device.

SNMP Settings:

- **Port number**: The port of the connected device, by default *161.*
- **Get community string**: The community string needed to read from the device.
- **Set community string**: The community string needed to set to the device.

## Usage

### General

This page displays information regarding the **Control Center, Media Center, Sequence Generator Interplay** and **Migrate Archive** running status.

### Agent

This page displays the following page buttons, which open a new page with information regarding the running state of each agent's parameter group.

- Image Grabber
- KeyFrame Generator
- VolGen
- KeyFrame Consolidator
- Trim HighRes
- Clip Transfer
- Metadata Exchange Avid
- WF Host
- Transfer Avid TM
- Meta Worker
- XML Export
- Auto Planjob Match
- Edl Genrator Avide Roughcut
- Audio Exchanger
- DVD Image Creator
- Send Email
- Fuser AME
- Common Index Creator
- Tec Data Reader
- Restore Diva CTRL
- Archive Diva CTRL
- Vantage Direct Control
- HighRes Switcher
- Image Preview Generator
- Transfer Avid Wrapper
- Transfer EVS XSquare
- Router Control

### Server

This page displays the following page buttons, which open a new page with information regarding the running state of each server's parameter group.

- Query Service
- Media Request Service
- Transfer Service
- Retrieve Log Files
- IFinder Searcher
- IFinder Index Writer
- Workflow Management Status

### Watchdog

This page displays the following page buttons, which open a new page with information regarding the running state of each watchdog's parameter group.

- XML Import Balancer
- Essence Balancer
- CJ Core Services
- Logfile Move
- Encoding Unit
- SNMP Trapper
- IFinder Event Log Observer
- Essence Streaming
- Delete Queue Calc
- PJob Export
- Balancer AVID
- Asset Eraser
- Deletion Data
- System Cleaner
- Cutlist Control
