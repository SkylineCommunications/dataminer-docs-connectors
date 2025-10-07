---
uid: Connector_help_Avid_NEXIS_Technical
---

# Connector technical documentation template

## About

This connector monitors NEXIS-related system events on the associated Avid NEXIS System Director.

## Configuration

### Connections

#### SNMP Connection

This connector uses a Simple Network Management Protocol (SNMP) connection and requires the following input during element creation:

SNMP CONNECTION:

- **IP address/host**: 192.168.54.41
- **Device address**: not required
SNMP Settings:

- **Port number**: 161
- **Get community string**: public
- **Set community string**: private

### Web Interface

The web interface is only accessible when the client machine has network access to the product.

## How to Use

### General

This page contains information about the system:

- **Product Name**: The name of the Avid NEXIS product line.
- **Version**: The version of the Avid NEXIS install.

### Status

This page contains information regarding the overall status of the system:

- **System Director State**: The state of the System Director.
- **Check Event Log**:  Information regarding the check event log flag.
- **Workspace Redistributing Count**: The current number of workspaces currently performing a redistribution.

### Performance

This page contains information on the overall system performance:

- **Megabytes Per Second**: Total megabytes per second for all connected clients.
- **Read Megabytes Per Second**: Total read megabytes per second for all connected clients.
- **Write Megabytes Per Second**: Total write megabytes per second for all connected clients.
- **Messages Per Second**: The number of messages per second the system director is processing.
- **Open Files**: How many open files are currently open.
- **Active Client Count**: The active client count.
- **Maximum Client Count**: The maximum active client count.

### Usage

This page contains system usage information:

- **Highest Disk Used Percentage**: The highest percent used across all disks.
- **Total System MB**: How total system megabytes.
- **Total Allocated MB**: How total allocated megabytes. Allocated size is the sum of all the workspace sizes.
- **Total Used MB**: How total system usage across all workspaces.
- **File Count**: How total number of files across all workspaces.
- **Folder Count**: The number of folders across all workspaces.
- **Workspace Count**: How total number of workspaces.
