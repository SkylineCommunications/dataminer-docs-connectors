---
uid: Connector_help_ZDF_Room_Switching_Manager_Technical
description: "Use the ZDF Room Switching Manager to configure two DataMiner-managed rooms, select a mode, and track sequence progress, step status, retries, and errors."
---

# ZDF Room Switching Manager

## About

The connector coordinates a switching sequence between two DataMiner-managed rooms. One room acts as **Master** and owns the sequence; the other acts as **Follower** and executes the steps assigned to it.

## Configuration

Configure the remote room's **host**, **port**, and **API token** on the element. The connector uses these details to check remote-room health and exchange switching requests over the DataMiner API.

## How to Use

Select a switching mode to start its configured sequence:

- **Maintenance** and **BaseConfig** pause when a blocking step fails. An operator can continue the sequence after addressing the issue.
- **Force** continues to the next step after a failure.

The element reports the sequence state and step progress. Its execution table shows each step's status, retries, and any error message.
